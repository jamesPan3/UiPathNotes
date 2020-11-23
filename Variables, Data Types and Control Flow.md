# Variables, Data Types and Control Flow

## Variables
Variables are containers that can hold multiple data entries (values) of the same data type. The value of a variable can change through external input, data manipulation or passing from one activity to another.

Variables are configured through their properties. You can set them in the Variables panel. The main properties in UiPath are:
- **Name**
    - It should be as descriptive as possible to make your automation easy to read by other developers and to save time.
- **Type**
    - Defines what kind of data can be stored in the variable. In UiPath, the type is declared when the variable is created, however there are some specific types that are more generic and can accommodate different types of data. More about variables types right below.
- **Default Value**
    - In general, variables have initial values that change throughout the process. If no initial value is assigned at the creation of the variable, there is generally a default rule that assigns a value.
- **Scope**
    - The part of the workflow in which the variable can be used. Some variables can be global, others local. In real automation scenarios, there are many variables in use. Making multiple variables unnecessarily global can cause efficiency issues as well as possibility for confusion.

## Arguments
In UiPath, the scope of a variable cannot exceed the workflow in which it was defined. Since business automation projects rarely consist of single workflows, arguments have to be used.

Arguments are very similar to variables – they store data dynamically, they have the same data types and they support the same methods. The difference is that they pass data between workflows, and they have an additional property for this – the direction from/to which the data is passed. The direction can be In, Out and In/Out.

## Data Types
- **Numeric**
    - **Int32** System.Int32 (signed integers): 10, 299, -100, 0x69
    - **Long** System.Int64 (long integers): 5435435343O, -11332424D
    - **Double** System.Double (allows decimals, 15-16 digits precision): 19.1234567891011
- **Boolean**
    - System.Boolean: Used to store one of two values – **true** or **false**.
- **Date and Time**
    - **DateTime** System.DateTime: Used to store specific time coordinates (mm/dd/yyyy hh:mm:ss). This kind of variable provides a series of specific processing methods (subtracting days, calculating time remaining vs. today, and so on). For example, to get the current time, assign the expression DateTime.Now to a variable of type DateTime.
    - **TimeSpan** System.TimeSpan: Used to store information about a duration (dd:hh:mm:ss). You can use it to measure the duration between two variables of the type DateTime. For example, you can save the time at the start of the process in one variable (of type DateTime), the time at the end in another (of type DateTime) and store the difference in a variable of type TimeSpan.
- **String**
    - System.String: Used to store text. This type of data comes with many specific methods of processing, and will be addressed in depth in another lesson, namely Data Manipulation.
- **Collection**
    This category reunites all the collections of objects, with each object being identified through its index in the collection. Collections are largely used for handling and processing complex data. Some of the most encountered collections are:
    - **Array** ArrayOf<T> or System.DataType[]: used to store multiple values of the same data type. The size (number of objects) is defined at creation; 
    - **List** System.Collections.Generic.List<T>: used to store multiple values of the same data type, just like Arrays. Unlike Arrays, their size is dynamic;
    - **Dictionary** System.Collections.Generic.Dictionary<TKey, TValue>: used to store objects in the form of (key, value) pairs, where each of the two can be of a separate data type.
- **GenericValue**
    - This is a UiPath proprietary variable type that can store any kind of data, including text, numbers, dates, and arrays. This type is mainly used in activities in which we are not sure what type of data we will receive, yet in general the use of this is temporary.