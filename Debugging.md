# Debugging

## What is it?
Let's have a quick look at the new debugging features in 2019.10:
- The Debug File or Debug Project, Run File or Run Project options are now states of the same button in the ribbon.
- The Locals panel shows the values for arguments, the properties of the current and those of the previously executed activity. The values of variables and arguments can be modified from this panel. The design of the panel has been improved.
- You can right click variables or arguments in the Locals panel to add them to the Watch panel.
- Details about the thrown exception are displayed in the Locals panel.
- The Immediate panel lets you evaluate expressions you define during debugging to inspect data.
- You can monitor the execution of activities, containers and project files by using the Call Stack panel. This panel allows for easy access to the activity which threw an exception.
- When working with breakpoints, you can now add conditions, a hit count and log a message when hit. 
- Activities can now be tested either inside the workflow using the Test Activity context menu option, or from the Activities panel by creating a test bench.
- Run to this Activity and Run from this Activity context menu options start debugging the workflow to and from a certain activity.
- Use the Restart ribbon option to restart the debugging process from the first activity in the process or the activity from which the Run from this Activity option was triggered.
- The new Step Out action finishes the execution of the current activity and returns to the level of the container, pausing the debugging process.
- Whenever an exception is encountered during debugging, you can Break, Ignore the error and Continue. The Retry option re-executes the previous activity, and throws the exception if it's encountered again. These actions are now available in the Debug tab.

## Why do you need it?
The new approach will make it easier for you to build reliable workflows faster.