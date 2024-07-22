# Event Manager Company: Software QA Analyst/Developer Onboarding Assignment



## Submission Requirements

To complete this assignment, submit the following:

1. **GitHub Repository Link**: Ensure that your repository is well-organized and includes:
  - Links to five closed issues, each with accompanying test code and necessary application code modifications.
  - Each issue should be well-documented, explaining the problem, the steps taken to resolve it, and the outcome. Proper documentation helps others understand your work and facilitates future maintenance.
  - All issues should be merged into the main branch, following the Git workflow and best practices.

2. **Updated README**: Replace the existing README with:
  - Links to the closed issues, providing easy access to your work.
  - Link to project image deployed to Dockerhub.
  - A 2-3 paragraph reflection on what you learned from this assignment, focusing on both technical skills and collaborative processes. Reflect on the challenges you faced, the solutions you implemented, and the insights you gained. This reflection helps solidify your learning and provides valuable feedback for improving the assignment in the future.

## Grading Rubric

| Criteria                                                                                                                | Points |
|-------------------------------------------------------------------------------------------------------------------------|--------|
| Resolved 5 issues related to username validation, password validation, and profile field edge cases                      | 30     |
| Resolved the issue demonstrated in the instructor video                                                                 | 20     |
| Increased test coverage to 90% by writing comprehensive test cases                                                      | 20     |
| Followed collaborative development practices using Git and GitHub (branching, pull requests, code reviews)              | 15     |
| Submitted a well-organized GitHub repository with clear documentation, links to closed issues, and a reflective summary | 15     |
| **Total**                                                                                                               | **100**|

## Fixes performed:

1. FAILED tests/test_schemas/test_user_schemas.py::test_user_base_valid - KeyError: 'nickname'
2. FAILED tests/test_schemas/test_user_schemas.py::test_user_create_valid - KeyError: 'nickname'
3. FAILED tests/test_schemas/test_user_schemas.py::test_user_update_valid - KeyError: 'first_name'
4. FAILED tests/test_schemas/test_user_schemas.py::test_login_request_valid - pydantic_core._pydantic_core.ValidationError: 1 validation error for LoginRequest
5. FAILED tests/test_schemas/test_user_schemas.py::test_user_response_valid - AssertionError: assert UUID('449b6ef4-dc17-480a-9169-5ea21c40011f') == '449b6ef4-dc17-480a-9169-5ea21c40011f'

![image_2024-07-22_175526432](https://github.com/user-attachments/assets/1c53ca84-1803-4fda-9602-38ce899420a0)

## Test_user_Schemas

To fix these errors, I first needed to ensure that the test data includes all required fields and that the data types and formats are correct. 
Here are the steps to address each error:

1. KeyError: 'nickname' in test_user_base_valid and test_user_create_valid:
Ensure that the nickname field is included in the user_base_data and user_create_data test fixtures.

2. KeyError: 'first_name' in test_user_update_valid:
Ensure that the first_name field is included in the user_update_data test fixture.

3. ValidationError for UserResponse schema:
Ensure that the id field in user_response_data is a valid UUID string.

4. ValidationError for LoginRequest schema:
Ensure that the email field is included in the login_request_data test fixture instead of username.

5. For test_userr_response_valid, id in user_response_data is a string, but the UserResponse model expects it to be a UUID object. When you assert the equality of user.id and user_response_data["id"], you're comparing a UUID object with a string, which causes the AssertionError. To fix this, I first ensured that the id in user_response_data is a UUID object before performing the assertion. Then I modified the test fixture to convert the id field to a UUID object.

