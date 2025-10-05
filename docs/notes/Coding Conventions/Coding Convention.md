# Coding Convention

## Table of Contents

- [Coding Convention](#coding-convention)
  - [Table of Contents](#table-of-contents)
  - [**What is Coding Convention**](#what-is-coding-convention)
  - [**General Guidelines**](#general-guidelines)
  - [**Rules**](#rules)
    - [**Classes and Structs**](#classes-and-structs)
    - [**Functions/Methods**](#functionsmethods)
    - [**Variables**](#variables)
    - [**Formatting**](#formatting)
    - [**Semantics**](#semantics)
  - [**Checklist**](#checklist)

## **What is Coding Convention**
Coding Convention is a set of rules that states how the code should be written. The idea behind a coding convention is to make the code:

1.  Readeble
2.  Uniform (multiple people will write code in the same fashion)

Readable code helps developers avoid hard-to-find bugs and saves development time, as well as sanity.
Uniform code helps other parties (new members) to understand code faster and get the intention behind the code.

## **General Guidelines**
1. Prefer simple code that states intention rather than instruction
2. Prefer slower but more simpler and readable code, optimize only when necessary
> "Premature optimization is the root of all evil"
> 
> ~ Donald Knuth in his *Structured Programming With Go To Statements* paper

3. Prefer a larger number of short methods/functions over a small number of long methods
4. Use meaningful names i.e. `numberOfTicks`, `isDone` over `i`, `aa`, `ctr`, `num`

## **Rules**

:::caution **IMPORTANT**

- **MUST** and **MUST NOT/NEVER** - Must always be obeyed, no exceptions
- **SHOULD** - Try to obey as much as possible, but exceptions are allowed
- **CAN/COULD** - Try **not** to use too much, but not prohibited

:::
  
### **Classes and Structs**

- **RULE 1** - All classes and structs **MUST** use [*pascal case*](https://www.pluralsight.com/blog/software-development/programming-naming-conventions-explained#pascal-case)

:::tip **GOOD**

```csharp
class Program
{
   /* ... */
}

struct Image
{
   /* ... */
}

class BankingAccount
{
   /* ... */
}
```

:::

:::danger **BAD**

```csharp
// First letter is not uppercase, not `pascal case`
class program
{
   /* ... */
}

// First letter is not uppercase letter
struct _image
{
   /* ... */
}

// Not prohibited, but the use of underscores `_` should be limited
class Banking_Account
{
   /* ... */
}
```

:::

### **Functions/Methods**
- **RULE 2** - Methods **MUST** be `private` unless they are accessed outside the class, when they must be `public` ([Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)))
- **RULE 3** - All methods **MUST** use `pascal_case`
- https://www.pluralsight.com/blog/software-development/programming-naming-conventions-explained#pascal-case

:::tip **GOOD**

```csharp
private void DoSomeWork()
{

}
```

:::

:::danger **BAD**

```csharp
private void doSomeWork()
{

}

private void Do_Some_Work()
{

}

private void do_some_work()
{

}
```

:::

### **Variables**
- **RULE 4** - Member variables use `pascal case` (same as classes, structs and methods) but *local variables* **MUST** use `camel case`
  - `camel case` is similar to the `pascal case` but it start with a lowercase letter
  - https://www.pluralsight.com/blog/software-development/programming-naming-conventions-explained#camel-case


:::tip **GOOD**

```csharp
class Program
{
   // Member variable
   private readonly int NumberOfIterations = 3;

   public static void Main()
   {
      // Local variables
      int i = 3;
      int inputNumber = 3;
   }
}
```

:::

:::danger **BAD**

```csharp
class Program
{
   // Member variable
   private readonly int numberOfIterations = 3;
   private readonly int number_of_iterations = 3;

   public static void Main()
   {
      // Local variables
      int input_number = 3;
      int InputNumber = 3;
      int Input_Number = 3;
   }
}
```

:::

### **Formatting**

- **RULE 5** -  Lines **SHOULD** be shorter than 120 characters (so they don't disappear off the screen)


:::tip **GOOD**

```csharp
private static void DoSomeCalculations(
   int arg1, int arg2, int arg3, int arg4, 
   int arg5, int arg6, int arg7, int arg8, 
   int arg9, int arg10, int arg11, int arg12
);
```

:::

:::danger **BAD**

```csharp
// Line too long, must be scrolled
private static void DoSomeCalculations(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6, int arg7, int arg8, int arg9, int arg10, int arg11, int arg12);
```

:::

- **RULE 6** - *Allman* convention **MUST** be used for bracket (`{` and `}`) placement
   -  https://en.wikipedia.org/wiki/Indentation_style#Brace_placement_in_compound_statements
   -  https://en.wikipedia.org/wiki/Indentation_style#Allman_style
   -  Each brace (both `{` and `}`) starts on a new line and is the only character on that line

:::tip **GOOD**

```csharp
if(a > b)
{
   /* CODE */
}
else
{
   /* CODE */
}
```

:::

:::danger **BAD**

```csharp
if(a > b) {
   /* CODE */
} else {
   /* CODE */
}

if(a > b)
{ /* CODE */ } else {
   /* CODE */
}

if(a > b){
   /* CODE */
} else
{
   /* CODE */ }
```

:::

- **RULE 7** - Braces `{}` **MUST NEVER** be omitted in `if`, `else`, `while`, `for` (etc.) blocks, even when the block contains only one statement

:::tip **GOOD**

```csharp
if(a > b)
{
   b = a - b;
   a = a + 1;
}

while(!done)
{
   DoSomeWork();
}

for (int i = 0; i < 3; i++)
{
   Console.WriteLine(2*i);
}
```

:::


:::danger **BAD**

```csharp
while(!done) DoSomeWork();

while(!done)
DoSomeWork();

while(!done)
   DoSomeWork();

for (int i = 0; i < 3; i++)
Console.WriteLine(2*i);
```

:::

- **RULE 8** - Each block **MUST** be indented one *TAB* to the right

:::tip **GOOD**

```csharp
class Program
{
   public static void Main()
   {
      while(!done)
      {
         DoSomething();
         if(cancellationRequested)
         {
            break;
         }
      }
   }
}
```

:::

:::danger **BAD**

```csharp
class Program
{
public static void Main()
{
   while(!done)
   {
      DoSomething();
if(cancellationRequested)
{
   break;
}
   }
}
}
```

:::

### **Semantics**

- **RULE 9** - If a fuction returns something, it **MUST NEVER** be ignored
  - If you do not care about the return value, you **MUST** explicitly use the discard operator `_`
  - https://softwareengineering.stackexchange.com/a/433117


:::tip **GOOD**

```csharp
private int DoSomeOperation(int a, int b)
{
   return a + b;
}

public static void Main()
{
   // This is good practice.
   // We want anybody reading our code to know we didn't forget
   //    about the return value of the `DoSomeOperation`, we just don't care about it.
   // `_` is a discard operator in C# 
   _ = DoSomeOperation(2, 3);
}
```

:::

:::danger **BAD**

```csharp
private int DoSomeOperation(int a, int b)
{
   return a + b;
}

public static void Main()
{
   // This is valid C# but not good practice, we ignore the returned value.
   // Maybe we forgot to get the result ???
   DoSomeOperation(2, 3);
}
```

:::

- **RULE 10** - Each declaration **MUST** be written on its own line.

:::tip **GOOD**

```csharp
int a;
int b = 3;
ConcurrentCode object = new ConcurrentCode();
ConccurentCode object2 = new ConccurentCode();
```

:::

:::danger **BAD**

```csharp
int a, b = 3;
ConcurrentCode object, object2;
```

:::

- **RULE 11** - Good comment answers the question *WHY?* Bad comment answers the question *WHAT?*


:::tip **GOOD**

```csharp
public static void Main()
{
   // GOOD COMMENT:
   // Camera API v1.0.4 requires that the byte `0x03` is sent
   //    before ending the communication.
   // See http://www.some-camera.com/model-t/documents/manual/1.0.4/api#close
   camera.SendByte(0x03);
   camera.Close();
}
```

:::

:::danger **BAD**

```csharp
public static void Main()
{
   // BAD COMMENT:
   // Send HEX 3 to camera
   camera.SendByte(0x03);
   camera.Close();
}
```

:::


## **Checklist**

Use this checklist to check your code before submission:

- [ ] **RULE 1** - All classes and structs **MUST** use `pascal case`
- [ ] **RULE 2** - Methods **MUST** be `private` unless they are accessed outside the class, when they must be `public`
- [ ] **RULE 3** - All methods **MUST** use `pascal case`
- [ ] **RULE 4** - Member variables use `pascal case` but *local variables* **MUST** use `camel case`
- [ ] **RULE 5** - Lines **SHOULD** be shorter than 120 characters
- [ ] **RULE 6** - *Allman* convention **MUST** be used for bracket (`{` and `}`) placement
- [ ] **RULE 7** - Braces `{}` **MUST NEVER** be omitted in `if`, `else`, `while`, `for` (etc.) blocks
- [ ] **RULE 8** - Each block **MUST** be indented one *TAB* to the right
- [ ] **RULE 9** - If a fuction returns something, it **MUST NEVER** be ignored
- [ ] **RULE 10** - Each declaration **MUST** be written on its own line.
- [ ] **RULE 11** - Good comment answers the question *WHY?* Bad comment answers the question *WHAT?*
