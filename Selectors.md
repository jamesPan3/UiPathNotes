# Selectors
## What are Selectors?
A Selector in UiPath Studio is a feature that enables the **identification** of the User Interface elements through its **address and attributes** stored as XML fragments. The element identification is done to perform specific activities in an automation project. Selectors are generated automatically every time we use an activity that interacts with graphical user interface elements.

We can think of the **element identification process** achieved through Selectors as a postman that delivers letters to a certain address. In order for the postman to deliver the letters, a specific path is required and must contain **structured and hierarchized details** such as Country > City > Zip Code > Street Name > Street Number > Apartment Number. Similarly, UiPath Studio requires the detailed path to a specific element within the user interface.

## The Structure of Selectors
User interfaces (UIs) are built using a series of containers nested one inside the other. Let’s take the example of a selector for the First name input field in MyCRM Application, and try to understand the meaning of the structure.
![Selector Structure](assets/Ckwm6E49rTsaa_vG_ggIDmh7P1RvAu1Zj.png "Selector Structure")