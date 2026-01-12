# White Box Testing Notes

## What is White Box Testing?

White Box Testing examines the software’s internal logic, structure, and code behavior to ensure correct input-output flow, code reliability, and security.

This technique provides visibility into an application’s internal mechanisms to:
- Validate logic paths
- Optimize performance
- Detect vulnerabilities

---

## What do you verify in White Box Testing?

White Box Testing involves verifying the software code for the following:

- Internal security holes  
- Broken or poorly structured coding paths  
- Flow of specific inputs through the code  
- Expected output  
- Functionality of conditional loops  
- Testing of each statement, object, and function individually  

---

## How do you perform White Box Testing?

**STEP 1: Understand the Source Code**  
The tester must be highly familiar with the source code and secure coding practices.

**STEP 2: Create and Execute Test Cases**  
Test the application’s source code for proper flow and structure by writing and executing dedicated test code.

---

## White Box Testing Techniques

A major White Box Testing technique is **Code Coverage Analysis**.  
It identifies areas of a program that are not executed by a set of test cases.

Once gaps are identified, additional test cases are created to verify untested parts of the code, improving overall software quality.

### Common White Box Testing Techniques

- Statement Coverage  
- Decision Coverage  
- Branch Coverage  
- Condition Coverage  
- Multiple Condition Coverage  
- Finite State Machine Coverage  
- Path Coverage  
- Control Flow Testing  

---

### Statement Coverage

Statement Coverage requires that every executable statement in the code is tested at least once.

![Statement Coverage](https://github.com/user-attachments/assets/a83a4400-3a0e-44e2-918b-f3885929a3b2)

**What is covered by Statement Coverage?**
1. Unused Statements  
2. Dead Code  
3. Unused Branches  
4. Missing Statements  

---

### Branch Coverage

Branch Coverage ensures that every possible branch (if, else, loops, and conditional paths) is executed at least once.

![Branch Coverage](https://github.com/user-attachments/assets/25d707f5-1620-451f-85b5-2f3cd055845f)

**Note:**  
Using Statement Coverage and Branch Coverage generally achieves **80–90% code coverage**, which is considered sufficient in most projects.

---

## Code Coverage vs Functional Coverage

| Code Coverage | Functional Coverage |
|--------------|--------------------|
| Measures how much source code is executed | Measures how much functionality is tested |
| Does not use design specification | Uses design specification |
| Mostly done by developers | Mostly done by testers |

---

## Code Coverage Tools

| Tool Name | Description |
|---------|------------|
| Cobertura | Open-source tool that measures test coverage by instrumenting code and analyzing executed vs non-executed lines |
| Others | JaCoCo, SonarQube, Emma, etc. |

---

## Advantages and Disadvantages of Code Coverage

### Advantages
- Provides a quantitative measure of code coverage  
- Helps create additional test cases to increase coverage  
- Identifies untested areas of the code  

### Disadvantages
- May show 100% coverage even if features are missing  
- Does not confirm testing of all possible input values  
- Does not measure quality or logic correctness  
- Cannot detect missing requirements from specifications  

---

## What are the Different Types of White Box Testing?

- **Unit Testing** – Testing individual units or blocks of code  
- **Testing for Memory Leaks** – Identifies memory mismanagement issues  
- **White Box Penetration Testing** – Full access testing to expose security threats  
- **White Box Mutation Testing** – Modifies code to evaluate test effectiveness  

---

## White Box Testing Tools

- EclEmma  
- NUnit  
- PyUnit  
- HTMLUnit  
- CppUnit  

---

## Best Practices in White Box Testing

To achieve high-quality and secure code, follow these best practices:

- **Know the Code** – Understand logic, flow, and dependencies  
- **Automate Early** – Use JUnit, pytest, and CI/CD pipelines  
- **Measure Coverage Wisely** – Target 80–90% coverage  
- **Test Edge Cases** – Validate boundary values and exceptions  
- **Combine Testing Types** – Use Black Box and Gray Box Testing  
- **Maintain Documentation** – Keep tests updated as code evolves  

---

## Common Mistakes in White Box Testing

- Chasing 100% coverage without quality improvement  
- Ignoring security-related code paths  
- Poor test maintenance  
- Testing only in isolation  
- Skipping peer code reviews  

---

## White Box vs Black Box vs Gray Box Testing

- **White Box Testing**  
  Focuses on internal code structure, logic, and data flow.

- **Black Box Testing**  
  Focuses on functionality without knowledge of internal code.

- **Gray Box Testing**  
  Combines partial code knowledge with functional testing.

**In summary:**  
- White Box = Code-level accuracy  
- Black Box = User-level validation  
- Gray Box = Balanced approach for better coverage
