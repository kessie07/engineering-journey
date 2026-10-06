# AI Customer Support Automation

**Status:** Built / worked on (3-person team project)
**Stack:** Django + ML
**Code:** Not in my current workspace yet

## What it does

Takes an incoming support ticket and works out what to do with it:

1. **Classify** the ticket's intent / category
2. **Predict its priority**
3. **Retrieve similar past cases** from ticket history
4. **Generate a suggested response** or recommendation
5. **Route it**: either `AUTO_REPLY` or send it to a human for review

## Human in the loop

The system doesn't reply to everything on its own. Some tickets go out as `AUTO_REPLY`. The rest are routed to a person for review, with the suggested response and similar past cases there to help, so a human still makes the call.

## My part

I mainly worked on the **ML side**, plus **frontend and integration work** to connect it to the Django app.

## Next

Pull the code into my workspace and write up the ML side properly: which models we used and how we evaluated them.
