# Selectors
## What are Selectors?
A Selector in UiPath Studio is a feature that enables the **identification** of the User Interface elements through its **address and attributes** stored as XML fragments. The element identification is done to perform specific activities in an automation project. Selectors are generated automatically every time we use an activity that interacts with graphical user interface elements.

We can think of the **element identification process** achieved through Selectors as a postman that delivers letters to a certain address. In order for the postman to deliver the letters, a specific path is required and must contain **structured and hierarchized details** such as Country > City > Zip Code > Street Name > Street Number > Apartment Number. Similarly, UiPath Studio requires the detailed path to a specific element within the user interface.

## The Structure of Selectors
User interfaces (UIs) are built using a series of containers nested one inside the other. Let’s take the example of a selector for the First name input field in MyCRM Application, and try to understand the meaning of the structure.

## Tags & Attributes of Selectors
As you saw, selectors are made of nodes. And each node is made of tags and attributes. Let's take an example to explain the two. Below is a selector node.

### Tags
- Nodes in the selector XML fragment
- Correspond to a visual element on the screen
- First node is the app window
- Last node is the element itself

For example:
- **wnd** (window)
- **html** (web page)
- **ctrl** (control)
- **webctrl** (web page control)
- **java** (Java application control)

### Attributes
Every attribute has a name and a value. You should use only attributes with constant or known values.

For example:
- parentid=‘slide-list-container’
- tag=‘A’
- aaname=‘Details’
- class=‘btn-dwnl’