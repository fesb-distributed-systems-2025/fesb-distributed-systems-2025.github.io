# Creating a Web API
# Lab 5: HTTP Programming

## **Table of Contents**

- [Creating a Web API](#creating-a-web-api)
- [Lab 5: HTTP Programming](#lab-5-http-programming)
  - [**Table of Contents**](#table-of-contents)
    - [**Creating a new Web API Project**](#creating-a-new-web-api-project)
    - [**Creating a new Controller**](#creating-a-new-controller)

### **Creating a new Web API Project**

To create a new API project:

1. Open *Visual Studio 2022* and select *Create New Project*

![web-api-new-project](./web-api-new-project.PNG)

2. Choose *ASP.NET Core Web API* as the project type

![web-api-new-project-type](./web-api-new-project-type.PNG)

3. Enter the name of the project and where it will be saved and then click *Next*

![web-api-configure](./web-api-configure.PNG)

4. **IMPORTANT:**
   - Choose *.NET 6.0* or *.NET 7.0* for the *framework* 
   - Uncheck *Configure for HTTPS*
   - Uncheck *Enable Docker*
   - Check *Use controllers (uncheck to use minimal APIs)*
   - Check *Enable OpenAPI support*

![web-api-new-additional-info](./web-api-new-additional-info.PNG)

**After this, you get an ASP.NET Web API project with one sample controller that can be deleted.**

![web-api-controllers](./web-api-controllers.PNG)

### **Creating a new Controller**

1. On the (probably) right side of the screen, where the *Solution Explorer* is, right click on the *Controllers* folder > *Add* > *Controller*
   
![web-api-controller-new](./web-api-controller-new.PNG)

2. On the left side of the dialog choose *API* and in the center choose *API Controller - Empty*

![web-api-controller-type](./web-api-controller-type.PNG)

3. Give the new controller a name **so that it ends with** *Controller* (e.g. *StudentController*)

![web-api-controller-name](./web-api-controller-name.PNG)

**After this, your new** (*StudentController*) **controller should be visible in the** *Soultion Explorer* **pane under** *Controllers* **folder**.
