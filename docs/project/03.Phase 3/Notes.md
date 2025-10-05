# Phase 3 - Notes

## Table Of Contents

- [Phase 3 - Notes](#phase-3---notes)
	- [Table Of Contents](#table-of-contents)
	- [**Steps for Creating a Basic WebAPI**](#steps-for-creating-a-basic-webapi)
	- [**Hints**](#hints)
		- [**General**](#general)
	- [Further Reading](#further-reading)


## **Steps for Creating a Basic WebAPI**

1. Pull master branch
	1. Git checkout master
	2. Git pull
	3. Git checkout dev
2. After merging PR, create tag 2.0.0 (git push --tags)
	1. Git checkout master
	2. Git tag 2.0.0
	3. Git push --tags
	4. Git checkout dev
3. Create Models folder
4. Move Email.cs model to Models folder
5. Create Logic folder
6. Create IEmailLogic interface in Logic folder
	1. Define CRUD methods in IEmailLogic
7. Create EmailLogic class in Logic folder
	1. Iherit from IEmailLogic
Implement all IEmailLogic methods
8. Add constructors
9.  Register singleton service [HINT](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07/blob/cd2e59e6ca4265b0ed48a8627b607d66ee20b671/Program.cs#L14)

## **Hints**

### **General**

- Refer to the [pkaselj-lab-07 GitHub Repo](https://github.com/fesb-distributed-systems-2024/pkaselj-lab-07) for reference implementation.
- Refer to the [pkaselj-lab-07-plus GitHub Repo](https://github.com/fesb-distributed-systems-2024/pkasel-lab-07-plus) for last year's full project implementation.
- Use [regexr](https://regexr.com/) to practise regular expressions

## Further Reading



