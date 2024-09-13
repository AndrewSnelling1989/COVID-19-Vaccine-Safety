# COVID-19-vaccine-safety
Statistical code for Covid-19 vaccine safety analyses

DOI: 10.5281/zenodo.13760918

## Papers details 
### Paper 1
>**Title:** Risk of thrombocytopenia and thromboembolism after covid-19 vaccination and SARS-CoV-2 positive testing: self-controlled case series study
>
>**DOI:** 10.1136/bmj.n1931
>
>**Paper authors:** Julia Hippisley-Cox, Martina Patone, Xue W Mei, Defne Saatci, Sharon Dixon, Kamlesh Khunti, Francesco Zaccardi, Peter Watkinson, Manu Shankar-Hari, James Doidge, David A Harrison, Simon J Griffin, Aziz Sheikh, Carol A C Coupland
>
>**Data source:** https://www.bmj.com/content/374/bmj.n1931

### Paper 2
>**Title:** Neurological complications after first dose of COVID-19 vaccines and SARS-CoV-2 infection
>
>**DOI:** 10.1038/s41591-021-01556-7
>
>**Paper authors:** Martina Patone, Lahiru Handunnetthi, Defne Saatci, Jiafeng Pan, Srinivasa Vittal Katikireddi, Saif Razvi, David Hunt, Xue W Mei, Sharon Dixon, Francesco Zaccardi, Kamlesh Khunti, Peter Watkinson, Carol A C Coupland, James Doidge, David A Harrison, Rommel Ravanan, Aziz Sheikh, Chris Robertson, Julia Hippisley-Cox
>
>**Data source:** https://www.nature.com/articles/s41591-021-01556-7

### Paper 3
>**Title:** Risks of myocarditis, pericarditis, and cardiac arrhythmias associated with COVID-19 vaccination or SARS-CoV-2 infection
>
>**DOI:** 10.1038/s41591-021-01630-0
>
>**Paper authors:** Martina Patone, Xue W Mei, Lahiru Handunnetthi, Sharon Dixon, Francesco Zaccardi, Manu Shankar-Hari, Peter Watkinson, Kamlesh Khunti, Anthony Harnden, Carol A C Coupland, Keith M Channon, Nicholas L Mills, Aziz Sheikh, Julia Hippisley-Cox
>
>**Data source:** https://www.nature.com/articles/s41591-021-01630-0

### Paper 4
>**Title:** Risk of myocarditis following sequential COVID-19 vaccinations by age and sex
>
>**DOI:** 10.1101/2021.12.23.21268276
>
>**Paper authors:** Martina Patone, Xue W Mei, Lahiru Handunnetthi, Sharon Dixon, Francesco Zaccardi, Manu Shankar-Hari, Peter Watkinson, Kamlesh Khunti, Anthony Harnden, Carol A C Coupland, Keith M Channon, Nicholas L Mills, Aziz Sheikh, Julia Hippisley-Cox
>
>**Data source:** https://www.ahajournals.org/doi/10.1161/CIRCULATIONAHA.122.059970

## Code details

>**Simulated dataset:** sample_sccs_csv, includes
>
>>***nimspatid:*** patient id (1:n)
>>
>>***vaccine_date_1:*** date of vaccine first dose
>>
>>***vaccine_date_2:*** date of vaccine second dose
>>
>>***vaccine_date_3:*** date of vaccine third dose
>>
>>***vaccine_type_1:*** type of vaccine first dose
>>
>>***vaccine_type_2:*** type of vaccine second dose
>>
>>***vaccine_type_3:*** type of vaccine third dose
>>
>>***date_positive:*** date of the earliest positive RC-PCR test
>>
>>***sample_date:*** date of earlist hospital admission or death from the outcome
>>
>>***onsdateofdeath:*** date of death
>>
>>***sample_ons:*** 1 if patient died drom the outcome on the death certificate
>>
>>***sample_period1:*** 1 if patients had the outcome in the study period
>
>Use **sample_master:** run all dofiles to format date, run the models and create table for results
>
>Need main folder ***OX107_sample_folder*** including 
>>***OX107_sample_folder/dofiles*** -- save dofiles
>>
>>***OX107_sample_folder/tables*** -- save tables as Stata datasets
>>
>>***OX107_sample_folder/caseseries*** -- save datasets
>>
>>***OX107_sample_folder/estimates*** -- save Stata estimates of the models
>>
>>***OX107_sample_folder/moderls*** -- save models results as Stata datasets
>>

### Funding
Health Data Research UK


