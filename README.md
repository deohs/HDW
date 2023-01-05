### Cleaning practices

- R Markdown script
- Version control done through Git utilizing GitHub
    - Clone the repo onto your computer
    - Do NOT save the data to your computer ever!
- Naming conventions
    - functions: camel case (myFunctionWorks)
    - original RedCap variables: lowercase with “_” between words (my_variable)
    - new variables: lowercase with “_” between words (my_variable)
        - new logical variable: end in “01” (my_variable_01)
        - new categorical/factor variable: end in “fac” (my_variable_fact)
- Keep old variable in dataset and write over them with clean data if doing minor cleaning
    - minor cleaning includes:
        - changing missing to NA or the equivalent for dates
        - correctly spelling a value
        - making a categorical variable into an ordered factor variable (RedCap cleaning script does a lot of this for us)
- Missing values
    - change all missing to NA
- Labeling- done through RedCap code. If you notice an error in the labeling please update.

### Documentation

- done before the chunk of code (in a Markdown file) that executes the cleaning
- original variable name
- new variable(s) name(s), if any
- any important cleaning steps
    - which values were changed to NA
    - which missing values were able to be filled
    - if the class of the variable was changed
- variable class
- Example of how documentation should look for variables
    - New variables: allergy
    - Variables used: allergies, allergies_v2, allergies_v3
    - Cleaning: convert to a factor and combine into one variable
    - Class: factor
    - Description: joint variable for “allergies variable”

### Cleaning steps done (or tbd) in the HDW_cleaning.Rmd file

1. Important variables to create before the rest of cleaning
    1. identifier- new ID variable for all enrollees (HDW-X#-S###)
    2. RedCap_id- new record_id variable for all enrollees (###)
    3. survey_date- date that the survey was administered (this is in progress, need to attend ITHS help to recover missing metadata)
    4. arm- “D”- dairy, “C”- community, “S”- switched
2. Data checks to do before the rest of cleaning
    1. identifier matching sample id numbers
        1. mismatched identifiers can be double checked by cross referencing date of appointment and the date of the samples (will be the date of the appointment)
    2. ensure there are not multiple forms for the same time point for each identifier (this could happen due to data entry errors and especially for those who switched between study arms)

### General variable cleaning considerations

1. Check for variable equivalents in another in other forms. This will be represented by a v# after the variable name. Ex. id_number, id_number_v2, id_number_v3
    1. if there are variable equivalents, coalesce these variables into one data ← data %>% mutate(identifier = coalesce(id_number, id_number_v2, id_number_v3).
        1. note: coalesce only takes the first value presented so this would not be appropriate to use when it is possible for there to be multiple values for the same record in the variables being coalesced. This should not be an issue for the variable equivalents because there will only be one filled in per record.
    2. check for if there is an “other” variable for that variable (race_other), which would be the write in for an option that would need to be added into the data.
2. Check all values- you can do this in a table or another summarizing manner
    1. note and fix, when possible, the any values outside of an expected range (ex: weight is 12)
        1. impossible values can be changed to NA unless there are variables around it that can be used to gather this variable
3. Check-all question types- note that these question types allow for multiple answers being selected and are exported in a different manner (race___01, race___02, race___03 etc)
    1. how to clean these variables,
        1. identify all the variables that correspond to this question
        2. coalesce the variables versions (the variable and their equivalent v#) that are the equivalent options for the different forms (race___01 and race___01_v3). You can coalesce these because there will only be one of these questions filled out due to the nature of how RedCap exports data.
        3. rename the logical values to be more descriptive for the variable (for race___01 which represents “white”, change the 1 to “white” and 0 to NA)
        4. combine all the checked boxes into one variable separated by commas (no coalesce, see note below)
            1. make sure there is no inconsistent ordering of the variables when you do this because you want two selected answers to always be written the same way (ex: “white, black” and “black, white” should not both be in the data otherwise they will be considered to be different values by R)
        5. rename the old variables if they will still be useful (race___01 could be renamed to “white_01”
    2. NOTE: these variables cannot be coalesced because the coalesce function only takes the first non NA value and would ignore any other selected values
