/*
filename OX107_sccs_descriptive.do
author	 JHC/MP/CC
date 	   5.1.2022
Notes	   derive numbers of events for each period
*/

** Defined in OX107_sample_globals
local first_outcome = "$first_outcome"
global variables = "1 2 3 4"

** Define globals in OX107_all_globals
foreach y in $study_outcomes_all {
			
** Open dataset
foreach x in $variables {
	foreach m in $models_all {
	
	** main
	use caseseries\OX107_caseseries_nims5_`y'_3dose, clear

	*** Overall 28 days 	
	do dofiles\OX107_caseseries_variables.do
	
** Generate risk interval 	
	gen group_week = exposed`x'
	lab values group_week exposed`x'
	
	gen group_overall = set`x'
	lab values group_overall set`x'
	
** remove patients who were not exposed (for each exposure) 
	bys nimspatid2: egen temp = sum(exposed`x')
	drop if temp == 0
  
** table counts for each model and outcome
	    if `m' == 1 {	
				capture collapse (sum) nevents if nevents==1, by(group_week)
				if _rc != 0 {
					continue
				}
				gen outcome = "`y'"
				rename group_week lab
				gen exposed =`x'
				order outcome exposed lab nevents
				gen model = `m'
				save tables\event_temp`m'`x'_`y',replace
			}

		if `m' == 20 {		
				capture collapse (sum) nevents if nevents==1, by(group_overall)
				if _rc != 0 {
					continue
				}
				gen outcome = "`y'"
				rename group_overall lab
				gen exposed =`x'
				order outcome exposed lab nevents
				gen model = `m'
				save tables\event_temp`m'`x'_`y',replace
				}
		}
}
}

	
** all exposure in one table per each model and outcome

foreach y in  $study_outcomes_all {
foreach m in  $models_all {

	use tables\event_temp`m'1_`y',clear
	gen dropit=1

		foreach x in $variables {
			capture append using tables\event_temp`m'`x'_`y'
				if _rc != 0 {
					continue
				}
		}
			
		drop if dropit==1
		drop dropit
		
		lab define exposed 1 "Oxford" 2 "Pfizer" 3 "Moderna" 4 "SARS-Cov-2" 0 "time period"
		lab values exposed exposed
		
		order model outcome exposed lab nevents 
		
		save tables\event_`y'_`m',replace 
}
}

** all exposure and outcome in one table per each model
foreach m in $models_all {
	use tables\event_`first_outcome'_1,clear
	gen dropit=1
	
		foreach y in $study_outcomes_all {
		capture append using tables\event_`y'_`m'
		if _rc != 0 {
					continue
				}
		}		
		drop if dropit==1
		drop dropit
		save tables\nims_table3_event_count_`m',replace
		order model outcome exposed lab nevents 
}


** all in one table
use tables\nims_table3_event_count_1,clear
gen dropit=1
	
	foreach m in $models_all {
	capture append using tables\nims_table3_event_count_`m'
	if _rc != 0 {
					continue
				}
	}
	
	drop if dropit==1
	drop dropit
	
save tables\count_by_exposed_all,replace


** tidy up
	local files1: dir "tables\" files "event_temp*.dta"
	cd "tables\"

	foreach x in `files1' {
		rm "`x'"
	}
	
	cd ..
