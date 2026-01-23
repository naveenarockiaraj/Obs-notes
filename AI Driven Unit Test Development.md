MOM - AI Driven Unit Test Development:  
  - Why we need to test?  
  - No test is better than bad test.Steps:  

- Which testing framework is suitable for this project? Analyze the codebase and package file before answering.
- Implement Vitest in this project.
- Write test case for the component one after the other.
- Optimize this test case for better readability and maintainability.
- Make sure all the test cases are getting success when new test case added.
- Fix the warnings.
- Test coverage is 100%.

Test-case Prompts:  

- Create me a non-bloated test case for this component with 100% coverage.
- Optimize this test case.
- Cleanup unused functions, variables and dummy test case.
- What does this test case do?

Test-case Prompting Guidance:  

- Run the test case coverage report to increase the coverage.
- Make sure the original component file is not modified for test case.
- In some edge cases we may need to change the source for testing.
- Always make sure all the test cases are getting success after changing the test case.
- Make sure irrelevant files are not changed/deleted.

- Don't test implementation details instead test the function I/p and O/p.
- Don't test third-party library internals.
- Don't test CSS styles.
- Don't test every prop combination if they don't affect behavior.

Models Used:  

- Claude Sonnet 4*
- GPT-5*
- Claude Sonnet 3.7
- Claude Sonnet 3.5

Official Docs:  

- Vitest similar to jest
- [https://vitest.dev/](https://vitest.dev/)
- [https://testing-library.com/docs/](https://testing-library.com/docs/)

  - Why not create all test cases at once?  
  -  Bloated  
  - Walkthrough of Test cases  
    - Mock  
    - Describe  
    - it  
    - BeforeEach, AfterAll  
    - expect (edited)