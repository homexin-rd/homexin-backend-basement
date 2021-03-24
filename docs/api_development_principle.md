# API Development Principles



## Template
1. Scenarios
    * Under what circumstances will this API be called?
    * Under what suspecious/ambiguous circumstances will this API NOT be called?
2. Assumptions
    * What assumptions do you hold when you develop this API? Note that assumptions are introduced to simplify situations yet pose underlying/potential troubles in the near future; hence, you are absolutely obligated to reveal them and further notify ones to pay more attention to them.
3. Input
    * What fields should be included when calling this API?
    * Please explicitly denote the at least OPTIONAL and NECESSARY properties.
4. Output
    * What fields should be included in the response?
    * If there are a variety of cases for repsonses, please provide a well-organized and clear list to demonstrate all of them.
5. Error cases
    * List all error cases, including expected and unexpected ones.
    * Always remember to take system errors into considerations.