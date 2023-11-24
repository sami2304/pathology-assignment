describe('Login Page - Positive Test Cases', () => {
  it('Should successfully log in with valid credentials', () => {
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('test@kennect.io');
    cy.get('#password').type('Qwerty@1234');
    cy.get('#loginButton').click();
    cy.url().should('include', '/home');
  });
});

**Negative Test Cases:**
```javascript
describe('Login Page - Negative Test Cases', () => {
  it('Should display an error message for invalid username', () => {
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('invalidUsername');
    cy.get('#password').type('Qwerty@1234');
    cy.get('#loginButton').click();
    cy.contains('Invalid username').should('be.visible');
  });

  it('Should display an error message for invalid password', () => {
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('test@kennect.io');
    cy.get('#password').type('invalidPassword');
    cy.get('#loginButton').click();
    cy.contains('Invalid password').should('be.visible');
  });

  it('Should display an error message for empty credentials', () => {
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#loginButton').click();
    cy.contains('Username and password are required').should('be.visible');
  });
});

#### B) Home Page:

**Positive Test Cases:**
```javascript
describe('Home Page - Positive Test Cases', () => {
  before(() => {
    // Perform a successful login before running these tests
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('test@kennect.io');
    cy.get('#password').type('Qwerty@1234');
    cy.get('#loginButton').click();
    cy.url().should('include', '/home');
  });

  it('Should display the list of todos', () => {
    cy.get('.todos-list').should('be.visible');
  });

  it('Should provide access to the Cost Calculator', () => {
    cy.get('#costCalculatorLink').click();
    cy.url().should('include', '/cost-calculator');
  });
});

**Negative Test Cases:**
describe('Home Page - Negative Test Cases', () => {
  before(() => {
    // Perform a successful login before running these tests
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('test@kennect.io');
    cy.get('#password').type('Qwerty@1234');
    cy.get('#loginButton').click();
    cy.url().should('include', '/home');
  });

  it('Should display a message for no todos', () => {
    // Log in with an account that has no todos
    // Validate that a message indicating no todos is present
  });

  it('Should not provide access to the Cost Calculator', () => {
    // Log in with an account that doesn't have access to the Cost Calculator
    // Validate that the link/button to access the Cost Calculator is not visible
  });
});


C) Cost Calculator for Blood Test:
Positive Test Cases:

describe('Cost Calculator - Positive Test Cases', () => {
  before(() => {
    // Perform a successful login before running these tests
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('test@kennect.io');
    cy.get('#password').type('Qwerty@1234');
    cy.get('#loginButton').click();
    cy.url().should('include', '/home');
  });

  it('Should calculate the cost of selected tests accurately', () => {
    // Navigate to the Cost Calculator
    // Select various blood tests and apply discounts
    // Verify that the calculated cost is accurate
  });

  it('Should apply discounts correctly', () => {
    // Navigate to the Cost Calculator
    // Apply different types and amounts of discounts
    // Ensure the final cost is updated accordingly
  });
});

Negative Test Cases:
describe('Cost Calculator - Negative Test Cases', () => {
  before(() => {
    // Perform a successful login before running these tests
    cy.visit('https://gor-pathology.web.app/');
    cy.get('#username').type('test@kennect.io');
    cy.get('#password').type('Qwerty@1234');
    cy.get('#loginButton').click();
    cy.url().should('include', '/home');
  });

  it('Should display an error message for no tests selected', () => {
    // Navigate to the Cost Calculator
    // Attempt to calculate the cost without selecting any tests
    // Verify that an appropriate message is displayed
  });

  it('Should display an error message for an invalid discount value', () => {
    // Navigate to the Cost Calculator
    // Apply an invalid discount value
    // Verify that an error message is displayed
  });
});
