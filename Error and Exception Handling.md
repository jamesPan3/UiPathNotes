# Error and Exception Handling

## Errors
Errors are events that a particular program can’t normally deal with. There are different types of errors, based on what's causing them - for example: 
- **Syntax errors**, where the compiler/interpreter cannot parse the written code into meaningful computer instructions.
- **User errors**, where the software determines that the user’s input is not acceptable for some reason.
- **Programming errors**, where the program contains no syntax errors, but does not produce the expected results. This are often called bugs.

## Exceptions
Exceptions are events that are recognized (caught) by the program, categorized and handled. More specifically, there is a routine configured by the developer that is activated when an exception is caught. Sometimes, the handling mechanism can be simply stopping the execution.

Some of the exceptions are linked to the systems used, while others are linked to the logic of the business process.

## Common Exceptions
- **NullReferenceException**, This error usually occurs when using a variable with no set value (not initialized).
- **IndexOutOfRangeException**, Occurs when the index of an object is out of the limits of the collection.
- **ArgumentException**, Is thrown when a method is invoked and at least one of the passed arguments does not meet the parameter specification of the called method.
- **SelectorNotFoundException**, Is thrown when the robot is unable to find the designated selector for an activity in the target app within the TimeOut period.
- **ImageOperationException**, Occurs when an image is not found within the TimeOut period.
- **TextNotFoundException**, Occurs when the indicated text is not found within the TimeOut period.
- **ApplicationException**, describes an error rooted in a technical issue, such as an application that is not responding.

## Try Catch
This activity catches a specified exception type in a sequence or activity, and either displays an error notification or dismisses it and continues the execution.

As a mechanism, Try Catch runs the activities in the Try block and, if an error takes place, executes the activities in the Catch block. The Finally block is only executed when no exceptions are thrown or when an exception is caught and handled in the Catch block (without being re-thrown).
- **Try**, The activities performed which have a chance of throwing an error.
- **Catch**, The activity or set of activities to be performed when an error occurs. Please note that multiple errors and corresponding activities can be added in this block.
- **Finally**, The activity or set of activities to be performed after the Try Catch block. This section is executed only when no exceptions are thrown or when an error occurs and is caught in the Catch section.

## Retry Scope
The Retry scope activity retries the contained activities as long as the condition is not met or an error is thrown.

The Retry Scope activity is used for catching and handling an error, which is why it’s **similar** to Try Catch. The **difference** is that this activity simply retries the execution instead of providing a more complex handling mechanism.

It can be used without a termination condition, in which case it will retry the activities until no exception occurs (or the provided number of attempts is exceeded).

### Additional Properties
- **NumberOfRetries**, The number of times that the sequence is to be retried.
- **RetryInterval**, Specifies the amount of time (in seconds) between each retry.

## ContinueOnError Property
Continue on Error is a property that specifies if the execution should continue even when the activity throws an error.

Keep in mind that, if the ContinueOnError is set to True on an activity that has a scope (such as Attach Window or Attach Browser), then all the errors that occur in other activities inside that scope are also ignored.

Having this property set to true is not recommended in all situations, but there are some situations in which it makes sense, such as:
- while using data scraping - so the activity doesn't throw an error on the last page (when the selector of the 'Next' button is no longer found).
- when we are not interested in capturing the error, but simply in the execution of the activity.

This field only supports Boolean values (True, False). The default value is False, thus, if the field is blank and an error is thrown, the execution of the project stops. If the value is set to True, the execution of the project continues regardless of any error.

## Global Exception Handler
The Global Exception Handler is a type of workflow designed to determine the behavior when encountering an execution error at the project level. This is why only one Global Exception Handler can be set per automation project.

Only **uncaught** exceptions will reach the Exception Handler. If an exception occurs inside a Try Catch activity and it is successfully caught and treated inside the Catch block (and not re-thrown), it will not reach the Global Exception Handler.

A Global Exception Handler can be created either by starting a new project with this type, or by setting an existing project as Global Exception Handler from the Project panel.

### How Does it Work?
The Global Exception Handler has 2 predefined arguments, that shouldn't be removed:
- errorInfo, with the In direction - contains the error that was thrown and the workflow that failed.
- result, with the Out direction - will store the next behavior of the process when it encounters the error.

The Global Exception Handler contains the predefined 2 actions below (that can be removed). Other actions can be added.
- **Log Error**, This part simply logs the error. The developer gets to choose the logging level: Fatal, Error, Warning, Info, and so on.
- **Choose Next Behavior**, Here the developer can choose the action to be taken when an error is encountered during execution:
    - Continue - The exception is re-thrown;
    - Ignore - The exception is ignored, and the execution continues from the next activity;
    - Retry - The activity which threw the exception is retried;
    - Abort - The execution stops after running the current handler.