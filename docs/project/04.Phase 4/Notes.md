# Phase 4 - Notes

## Table Of Contents

- [Phase 4 - Notes](#phase-4---notes)
  - [Table Of Contents](#table-of-contents)
  - [**Steps for Creating a Basic WebAPI**](#steps-for-creating-a-basic-webapi)
    - [**Preparation**](#preparation)
    - [**Error Handling**](#error-handling)
    - [**Data Transfer Objects - DTOs**](#data-transfer-objects---dtos)
    - [**Configuration**](#configuration)
  - [**Hints**](#hints)
    - [**General**](#general)
  - [Further Reading](#further-reading)


## **Steps for Creating a Basic WebAPI**

:::tip **Important notice:**
The instructions are written with *Email* domain in mind so the domain-specific examples are used. When applying these instructions to another domain e.g. *Trophy* make sure to rename the domain-specific names like `NewMailRequestDTO`, `MailDTO`, etc. to `NewTrophyRequestDTO`, `TrophyDTO`, etc.
:::

### **Preparation**

1. Pull master branch
    1. Git checkout master
    2. Git pull
    3. Git checkout dev
2. After merging PR, create tag 3.0.0 (git push --tags)
    1. Git checkout master
    2. Git tag 3.0.0
    3. Git push --tags
    4. Git checkout dev
   
### **Error Handling**
   1. Create *Exceptions* folder
   2. Create 3 Exception classes
   3. Create *Filters* folder 
   4. Create `ErrorFilter` class
   5. Copy filter code from the reference implementation (pkaselj-lab-07)
   6. Register filter by adding attributes to all controllers (extra points)
   7. Throw exceptions in the logic class

### **Data Transfer Objects - DTOs**
   1. Create new folder *DTO*
   2. Create new classes for DTOs
      1. One for `NewMailRequestDTO` - Used for CREATE and UPDATE request by the user for input
      2. One for `MailDTO` - Used by all operations (especially READ) to return information to the user
   3. Add fields/properties to the DTOs from the model
   4. Delete *JsonPropertyName* attributes from the model
   5. Edit controller to receive and return DTOs instead of models
   6. Modify controller code to create *Email* models from DTOs and vice versa
   
### **Configuration**
   1. Create a folder *Configuration*
   2. Create new class `DBConfiguration`
   3. Add a new JSON object "Database" in appsettings.json:
      1. Add "ConnectionString" property to the object
   4. Register configuration in `Program.cs`
   5. Inject configuration object in Repository class (in constructor)
   6. Save connection string value to the existing `_connectionString` object in the Repository class

## **Hints**

### **General**

- Refer to the [pkaselj-lab-07 GitHub Repo](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07) for reference implementation.
  - For more information on *implementing filters* refer to the associated [COMMIT](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07/commit/6041e551ba6f03ea6298dcea4e296c510f3a6b62)
  - For more information on *implementing DTOs* refer to the associated [COMMIT](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07/commit/d9c2712e5798b81bed13d995eb2e9b56da8ecd7d)
  - For more information on *implementing configuration* refer to the associated [COMMIT](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07/commit/6fad23d23fb3c0bac62e29978a0480d223557cf2)
  - For more information on *implementing DTO-model conversion methods* refer to the associated [COMMIT](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07/commit/369ebbe00aff2e45b23ea1eceac30fbdd70e91b0)
  - For more information on *implementing additional endpoints* refer to the associated [COMMIT](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07/commit/9d5c302217c1ea94cdf22943efbea276d1748c96)
- Refer to the [pkaselj-lab-07-plus GitHub Repo](https://github.com/fesb-distributed-systems-2024/pkasel-lab-07-plus) for last year's full project implementation.
- Use [regexr](https://regexr.com/) to practise regular expressions

## Further Reading



