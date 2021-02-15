# How to automate credit assignment on SONA

When making a study on SONA, you'll need to enter in your study's url (e.g., https://cogtoolslab.org:8881/index.html). However, this will only add your study to SONA but will not automatically assign credit to your participants after their participation. 

## First locate your SONA study's experiment_id and credit_token

To <b>automate</b> your credit assignment, add the following to the end of your url: ```?sona=1&survey_code=%SURVEY_CODE%``` 
(e.g., https://cogtoolslab.org:8881/index.html?sona=1&survey_code=%SURVEY_CODE%)

When you look at your study info, nagivate to the website section where you'll see a button "Sample Link with Embedded ID Code". 
If you click on this, you'll see that SONA will automatically assign a random number as your survey_code in the url. 
This survey_code will be different for every participant.

In study info, you'll also see Completion URLs for the client-side and server-side.
Click on the client-side url to view your study's unique experiment_id and credit_token. 
For example, the url might look like this: 

```
https://ucsd.sona-systems.com/webstudy_credit.aspx?experiment_id=1957&credit_token=94edbf1cbf524148b93e396bc6194eae&survey_code=XXXX
```

Where in this case, the experiment_id is: ```1957``` <br>
And the credit_token is: ```94edbf1cbf524148b93e396bc6194eae```

## Then add this info to the redirect link of your web experiment
