Date:   2012-09-15_162713

# Using Launch Center Pro to Create Sequential Tasks for Due App

This example uses [Launch Center Pro][1] to create a sequence of new [Due app][2] Tasks. 

## Use Case: Laundry Sucks

I hate doing laundry, and my wife hates nagging me to finish the entire process.  To maintain that loving feeling, I use a Launch Center Pro action that includes the first task title and a due://  URL.

    due:///add?title=Dry%20laundry%20[prompt-num]%20minutes%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20due%3A%2F%2F%2Fadd%3Ftitle%3Dfold%2520laundry%25205%2520PM
    
## How it Works

The Launch Center Pro Action will create the initial task. Once the task completed, Due app will prompt the user to open the embedded URL. With one confirmation tap, the second task is created.

## The URL

Writing the URL is simple: every task appended to the sequence requires and additional round of [percent encoding][3]. (There is one exception: do not encode the Launch Center Pro prompt brackets).

The second encoded URL now begins: 

    due%3A%2F%2F%2Fadd%3Ftitle%3D
    
And all the spaces (%20) in the second task name must have their percent sign encoded:
    
    %2520

## You Don't Have to Stop at Two


To add a third task, encode each percent sign a third time:

    due:///add?title=Dry%20laundry%20[prompt-num]%20minutes%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20due%3A%2F%2F%2Fadd%3Ftitle%3Dfold%2520laundry%25205%2520PM%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520due%253A%252F%252F%252Fadd%253Ftitle%253DVisit%252520Cold%252520One%252520City 

----
    
NB: The string of spaces separating two URLS are not required. It is for appearance only. For some reason, the Mac app ignores encoded carriage returns. If you're only using the iOS aps, you can replace all of the separating %20 and %2520 with %5Cr and %255Cr.


[1]: http://appcubby.com/launch-center/
[2]: http://www.dueapp.com
[3]: http://en.wikipedia.org/wiki/Percent-encoding
