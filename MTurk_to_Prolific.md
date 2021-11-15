# Transferring from Amazon Mechanical Turk to Prolific
This tutorial details how to take an online experiment that you have previously used [Amazon Mechanical Turk](https://www.mturk.com/) (AMT) to recruit participants and switch over to using [Prolific](https://www.prolific.co/) for participant recruitment instead.


## Step 1: Create a new study on Prolific
After logging in to Prolific, click "[new study](https://app.prolific.co/researcher/studies/new)":

<p align="center" style="font-size: smaller">
  <img width="85%" src="https://github.com/cogtoolslab/handy_tips/blob/master/images/prolific_new_study.png"></img><br/>
</p>

Fill in all the study details. After doing so, under "Study Link", paste the URL of your study and select the option "I'll use URL parameters":
<p align="center" style="font-size: smaller">
  <img width="85%" src="https://github.com/cogtoolslab/handy_tips/blob/master/images/prolific_url_params.gif"></img><br/>
</p>

Under "Study Completion" use the option "I'll redirect them using a URL":
<p align="center" style="font-size: smaller">
  <img width="85%" src="https://github.com/cogtoolslab/handy_tips/blob/master/images/prolific_completion_url.gif"></img><br/>
</p>

Fill in the other sections ("Audience", "Study Cost") as needed. 

## Step 2: Configure your study to collect Prolific parameters
Both AMT and Prolific fetch a similar set of variables from a URL query, and so collecting Prolific parameters, such as participant-level identifiers, will seem very familiar. 

Here is a table with the exact URL substrings that the query should find, as well as their equivalents on AMT:
| **URL Query Parts** | **AMT** | **Prolific** |
|---|---|---|
| Participant-level identifier  | workerId  | PROLIFIC_PID  |
| Study-level identifier  | hitId  | STUDY_ID  |
| Session-level identifier  | assignmentId  | SESSION_ID  |
| Where to submit*  | turkSubmitTo  | (doesn’t exist)  |

*This one is unique to AMT, and it always refers to the top-level domain, “https://www.mturk.com”

We can harvest these URL parameters via client-side javascript as follows:
```
// get experiment ID information from URL
var queryString = window.location.search;
var urlParams   = new URLSearchParams(queryString);
var prolificID  = urlParams.get('PROLIFIC_PID');    // ID unique to the participant
var studyID     = urlParams.get('STUDY_ID');        // ID unique to the study
var sessionID   = urlParams.get('SESSION_ID');      // ID unique to the particular submission
```

After successfully harvesting the URL parameters, you can then save it to your database as part of the trial information.

## Step 3: Manage study completion
Upon completion of the study, the participant must be directed to the URL specified under the "Study Completion" section of Prolific. 
The preferred way is to use a button at the end of the experiment, which, when clicked, redirects the participant to the completion URL. A line of code that does this is:
```
window.open("https://app.prolific.co/submissions/complete?cc=XXXXXXX","_self")
```
In the above line, the 'XXXXXXX' within the completion URL will be an alpha-numeric string that functions as the Completion Code for Prolific workers. You will have to manually copy this URL from Prolific's interface, and paste it into this line of your experiment code.

All that's left is to publish the study! After successful completion of the study, the participant's prolificID will automatically appear on the Prolific website in the 
"Active" tab, under the specified study name:
<p align="center" style="font-size: smaller">
  <img width="85%" src="https://github.com/cogtoolslab/handy_tips/blob/master/images/prolific_active_study.png"></img><br/>
</p>
<p align="center" style="font-size: smaller">
  <img width="85%" src="https://github.com/cogtoolslab/handy_tips/blob/master/images/prolific_active_study_2.png"></img><br/>
</p>

## Step 4 (optional): Prolific bonus payments
Bonusing on Prolific will require you to access the bonus scores as recorded in your databse (from the participant data stored during the experiments), to create
a csv file mapping the Prolific PROLIFIC_PID to the relevant bonus. That csv is then uploaded manually onto Prolific’s user interface to bulk-bonus participants with their
respective bonus money. This task has not yet been automated, but once it is, an explanation and sample code will be uploaded to this article.
<p align="center" style="font-size: smaller">
  <img width="85%" src="https://github.com/cogtoolslab/handy_tips/blob/master/images/prolific_bonus.png"></img><br/>
</p>

