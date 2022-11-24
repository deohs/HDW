Cleaning practices

- R Markdown script
- Version control done through Git utilizing GitHub
    - Cloned branches can be stored in prlab/unrestricted/Center Projects/Healthy Dairy Worker/Data and Analysis/REDCAP_data_cleaning/GitHub_Clones folder under name format “Lastname” or “Firstname” or on your computer as long as files aren’t moved or produced on your local drive
- Naming conventions
    - functions: camel case (myFunctionWorks)
    - original RedCap variables: lowercase with “_” between words (my_variable)
    - new variables: lowercase with “.” between words (my.variable)
        - new logical variable: end in “01” (my.variable.01)
        - new categorical/factor variable: end in “fac” (my.variable.fact)
        - new xxxxxx
- Keep old variable in dataset and write over them with clean data if doing minor cleaning
    - minor cleaning includes:
        - changing missing to NA or the equivalent for dates
        - correctly spelling a value
        - making a categorical variable into an ordered factor variable
- Missing values
    - change all missing to NA
    - dates
        - change dates that are not exact to be 1/1/YYYY if we have year
        - otherwise change to NAs
- Labeling- done through RedCap code, but Spanish needs to be removed
- Documentation
    - original variable name
    - new variable(s) name(s), if any
    - any important cleaning steps
        - which values were changed to NA
        - which missing values were able to be filled
        - if the class of the variable was changed
    - any values outside of an expected range (ex: weight is 12) and what was done with them, typically these can be changed to NA unless there are variables around it that can be used to gather this variable
    - variable class
- Example of how documentation should look for variables
    - Variables: allergies, allergies_v2, allergies_v3
    - convert to a factor (using RedCap code) and labeled

Resources for data cleaning and coding in R

1. [R for applied epidemiology and public health | The Epidemiologist R Handbook (epirhandbook.com)](https://epirhandbook.com/en/)
2. [Welcome | R for Data Science (had.co.nz)](https://r4ds.had.co.nz/index.html)
3. [The R Markdown Cheat Sheet - RStudio](https://www.rstudio.com/blog/the-r-markdown-cheat-sheet/)
4. RMarkdown
