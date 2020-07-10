---
title: Qualtrics URL Query String API
permalink: /simulation/docs/qualtrics-URL-query-string
parent: Simulation
---
Hi Natalie,

Thanks for your prompt response. I hope it is ok for me to CC my team members. We would like the users to input their email addresses, which would ideally be hashed into some identifier. Would it be possible to automatically generate the url links? In other words, what if the IRB question was a survey and when the users input their email address and hit submit, qualtrics would generate a url that is like:
the_program.com/c1?uid=h4sh12

Here “h4sh12” is their email address bob@smith.com run through a hashing function. Alternatively we could maybe just pass the email in directly (but url escaped), so qualtrics would generate

the_program.com/c1?uid=bob%40smith.com

We can then have the_program hash the email and pass it back to the qualtrics ending survey as a hash in the query string, to be stored in the survey using that query string to variable capture technique qualtrics already has

Thanks for your time on this! I’m more than happy to restate anything here or provide more info, or even speak on the phone if that is easier for you.

Cheers,
Misha

---
Hi Misha,

Yes, definitely ok! I've included them on this email as well.

Yes, it is possible to generate a unique URL link with their email address. You'll need to go through the following process to accomplish this task:

1. Create a text entry question where the respondent will input their email (or whatever identifier you want to use).

2.  Make a second question (make sure this question is in a separate "Block" from the above text entry question) you can paste the link to the second survey and add a query string to the end of this URL. This [support page](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/) outlines how to create that query string you are adding to the URL.

3. Go to  "Survey Flow" and add "Embedded Data". Use the "piped text" option to select the email (or whatever identifier you want to use) they input in the text entry question. Make sure to move that "Embedded Data" to the very top of the survey flow. This [other support page](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/embedded-data/) outlines how to use "Embedded Data".

Let me know if you have any more questions!

Best,

Natalie Dayton
qualtrics support

(801) 374-6682 support
qualtrics.com
