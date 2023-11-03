# TDD

> Eat your own dog food

Test your software as a user (consumer) would use it. If you write a REST API, then you should also test against the API endpoints. 
A test that needs to `GET` something from that API can also use the `POST` endpoint to add it first.

The tests are defined by the business requirements. We need tests that test those requirements. Therefore, if we don't have a test, then it wasn't a requirement.

A good practice is to create new models (copy) for the tests. If we do so, we indirectly also test the contract because if we need to change the models on the tests, then we also have to change the code on the consumer side.

--- 
Unit test are often an obstacle for refactorings (so much tests break, especially the ones that have many mocks) even though they should enable it.