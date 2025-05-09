# 🌿 Cypress Beginner Guide

A quick and beginner-friendly guide to get started with **Cypress** for testing web applications.

---

# 🚀 Cypress Test Automation Mastery

This repository provides a comprehensive roadmap from basic and intermediate to advanced Cypress concepts, complete with practical cheat sheets and structured learning materials. You'll find:

- **Essential references** for key test automation concepts
- **Structured learning path** from core selectors to CI/CD integration
- **Production-ready patterns** for building robust test frameworks
- **Quick-access cheat sheets** for daily test development

Whether you're looking to solidify fundamentals or implement advanced techniques like parallel execution and visual testing, this collection offers carefully organized resources to accelerate your Cypress mastery. The content progresses logically from element interaction strategies to full framework architecture, with practical examples at each stage.

## 📚 Topics We'll Cover

Here's the progression of concepts we'll explore, from core fundamentals to advanced techniques:

### 🎯 Core Concepts
1. **Selectors & Best Practices** - Locating elements efficiently
2. **Assertions** - Validating with `should` and `expect`
3. **Hooks** - Test lifecycle management (`before`, `beforeEach`, etc.)
4. **Custom Commands** - Creating reusable test commands

### 🛠️ Intermediate Techniques
5. **Fixtures** - Managing test data with JSON files
6. **Aliases & .then()** - Working with asynchronous operations
7. **Environment Variables** - Configuration with `Cypress.env()`
8. **Network Requests** - Handling APIs with `cy.intercept()`
9. **Stubbing & Mocking** - Simulating API responses
10. **Forms & Inputs** - Comprehensive form testing strategies

### 🚀 Advanced Topics
11. **File Operations** - Testing uploads/downloads
12. **Visual Testing** - Screenshots and video recording
13. **iframes** - Special handling for embedded content
14. **Cypress Studio** - GUI test generation

### ⚙️ Execution & Optimization
15. **Headless Mode** - CLI test execution
16. **Parallel Execution** - Speeding up test runs
17. **CI/CD Integration** - GitHub Actions, GitLab CI, etc.
18. **Cross-Browser Testing** - Running tests across browsers

### 🏗️ Architectural Patterns
19. **Real vs. Mock Data** - Testing strategies
20. **Page Object Model** - Scalable test architecture

Each topic includes practical examples and best practices to help you implement these concepts in real-world test automation projects.

---


# Basics ->

### 🌀 1. What is Cypress?

Cypress is a **JavaScript-based test automation tool** used to test web applications.

You can write tests that:

- 🌐 Visit web pages  
- ✍️ Click buttons, fill forms  
- ✅ Check if something is visible  
- 🔐 And make sure your app works as expected  

It’s mainly used for **End-to-End (E2E)** testing, but also supports **integration** and **component** testing.


### 🔥 2. Why Cypress?

- 💡 Easy to learn (if you know JavaScript)  
- ⚡ Fast & Real-time reloads  
- 🧪 Interactive GUI (you see what’s happening!)  
- 📦 Everything runs in the browser (no WebDriver needed)  
- 🧼 Clean syntax (`cy.get().click()`)


### 📦 3. How to Install Cypress

Run this in your project folder (Node.js required):

```bash
npm install cypress --save-dev
```

Then open Cypress GUI:

```bash
npx cypress open
```


### 📁 4. Cypress Folder Structure

Once Cypress is opened, it creates a cypress/ folder with:

- e2e/: where your test files go (*.cy.js)

- fixtures/: test data (JSON)

- support/: reusable commands

- cypress.config.js: configuration settings


### 🧪 5. Writing Your First Test

- Inside cypress/e2e/sample.cy.js, try this:

```js
describe('My First Test', () => {
  it('visits the site', () => {
    cy.visit('https://example.com')
    cy.contains('More information').click()
  })
})

```

---


## 🎬 After Writing Your First Cypress Test — What Next?

Once you’ve written your test file (example: cypress/e2e/my_first_test.cy.js), you’ll need to go back to the Cypress GUI and run it.
Here’s how it works:

✅ Step-by-Step:

### 1. Open Cypress GUI
If it’s not open, run this in your terminal:

```bash
npx cypress open
```

This will launch the Cypress Test Runner GUI.


### 2. Select the Type of Test

Cypress will ask:

🧪 "What type of testing do you want to do?"

Choose:
➡️ E2E Testing (End-to-End)

You might need to configure it the first time — just follow the prompt and click through.


### 3. 🧭 Pick Your Browser

When you run Cypress, it shows you a list like:

- Chrome  
- Edge  
- Electron  
- Firefox  

👉 **Choose your preferred browser** (usually **Chrome** is the most stable).


### 4. ▶️ Run Your Test File

Cypress now shows a list of test files inside the `cypress/e2e/` folder.

➡️ **Click on your test file** — for example:  
`my_first_test.cy.js`


### 5. 🎥 Watch the Magic!

The browser opens and shows your test running in **real-time**, like a screen recording.

You'll see:

- 🧾 Each Cypress command on the **left** (`cy.visit()`, `cy.get()`, etc.)
- 🖥️ What’s happening on the **screen** on the right
- ✅ **Green** = Passed
- ❌ **Red** = Failed


### 6.💡 Bonus Tip

While it's running, you can **hover over each command** on the left — it will **highlight what was selected or clicked** in the browser view.

🔍 It’s super helpful for **debugging**.


### 7. 🧪 Visual Summary

```bash
npx cypress open
↓
Choose: E2E Testing
↓
Pick: Chrome / Firefox / etc.
↓
Select your test file
↓
Watch test run in browser!
```

---


# Selectors ->

## 🔍 Selectors & Best Practices in Cypress (Easy + Deep + Fast)

A quick guide to mastering **element selection** in Cypress for reliable and maintainable tests.


### ✅ 1. What are Selectors in Cypress?

-Selectors are how you tell Cypress **which elements** to interact with on a webpage.

  Think of it like pointing at something and saying:
  "Hey Cypress, **click this button!**"  
  But you need to **point correctly** so Cypress finds the right element.


### 🧪 2. The Most Common Selectors in Cypress

```js
cy.get('button')           // Select by HTML tag
cy.get('.submit-btn')      // Select by class
cy.get('#username')        // Select by ID
cy.get('[name="email"]')   // Select by attribute
cy.get('[data-cy="login"]') // 🏆 Best practice: data-cy selector
```


### 🧠 3. Best Practices for Selectors

| DO ✅                          | DON'T ❌                              |
|--------------------------------|--------------------------------------|
| `data-cy="submit-btn"`         | `.btn-primary` (classes change)      |
| `[name="email"]`               | `#input-25` (auto-generated IDs)     |
| Short, readable selectors       | `div > form > div:nth-child(3) > button` |
| Reusable selectors             | Duplicated selectors everywhere      |


👉  Why data-cy is best?
Because it's only for testing - developers won't accidentally change it!

```html
<button data-cy="login-btn">Login</button>
```

```js
cy.get('[data-cy="login-btn"]').click()
```


### 🧰 4. Real-World Example

```html
<form>
  <input type="text" id="username" name="username" data-cy="username-input">
  <input type="password" id="password" name="password" data-cy="password-input">
  <button data-cy="submit-btn">Submit</button>
</form>
```

```js
cy.get('[data-cy="username-input"]').type('ramavtar')
cy.get('[data-cy="password-input"]').type('123456')
cy.get('[data-cy="submit-btn"]').click()
```


### 🔄 5. BONUS: Chaining and Traversing
Sometimes, you want to go deep inside elements. Example:

```js
cy.get('form').find('[data-cy="submit-btn"]').click()
```

or:

```js
cy.contains('Submit').click() // Select by visible text (very useful)
```


### 🧼 Summary Cheatsheet:

```js
cy.get('tag')              // By tag
cy.get('.class')           // By class
cy.get('#id')              // By ID
cy.get('[attr="value"]')   // By attribute
cy.get('[data-cy="xyz"]')  // ✅ Recommended for stable tests
cy.contains('text')        // By visible text
cy.get('parent').find('child') // Chaining
```

---

# Assertions ->

Let’s dive into Assertions in Cypress — what they are, how they work, and how to use them cleanly and quickly.

### 🎯 1. What Are Assertions?
Assertions are how you tell Cypress:
  -✅ "I expect this to be true!"
  -❌ If it’s not, the test fails.

They help you check if something happened as expected — like a button is visible, or text is correct.


### 🧪 2. Two Main Ways to Write Assertions

- ✅ Method 1: .should(...)

  ```js
  cy.get('button').should('be.visible')
  cy.get('.error-msg').should('contain', 'Invalid login')
  cy.get('input').should('have.value', 'Ramavtar')
  ```

- ✅ Method 2: .then() + expect(...) (for more control)
  
  ```js
    cy.get('.score').then(($el) => {
      expect($el.text()).to.equal('100')
    })
  ```


### 🧠 3. Common .should() Assertions

🎯 Common Cypress Assertions Cheat Sheet

| Assertion | Meaning | Example |
|-----------|---------|---------|
| `'be.visible'` | Element is visible | `cy.get('button').should('be.visible')` |
| `'exist'` | Element exists in DOM | `cy.get('#loader').should('exist')` |
| `'have.text', 'Welcome'` | Exact text match | `cy.get('h1').should('have.text', 'Welcome')` |
| `'contain', 'Ramavtar'` | Contains text | `cy.get('.user').should('contain', 'Ramavtar')` |
| `'have.class', 'active'` | Has CSS class | `cy.get('li').should('have.class', 'active')` |
| `'have.value', '123'` | Input value matches | `cy.get('input').should('have.value', '123')` |
| `'be.checked'` | Checkbox/radio is checked | `cy.get('[type="checkbox"]').should('be.checked')` |
| `'not.exist'` | Element doesn't exist | `cy.get('.toast').should('not.exist')` |

### 💡 4. Pro Tips:
- Chain multiple assertions:  
  ```js
  cy.get('button')
    .should('be.visible')
    .and('contain', 'Submit')
    .and('not.be.disabled')
  ```
  

### ⚙️ 5. Real Example: Login Form

```js
cy.get('[data-cy="username-input"]').type('ramavtar')
cy.get('[data-cy="password-input"]').type('123456')
cy.get('[data-cy="submit-btn"]').click()

// After submit, check welcome message
cy.get('[data-cy="welcome-msg"]').should('contain', 'Welcome, Ramavtar')
```


### 🔥 6. Bonus: Negation (not.)

```js
cy.get('.error-msg').should('not.exist')
cy.get('button').should('not.be.disabled')
```


### 🎁 7. Extra Power: .and() for chaining

```js
cy.get('button')
  .should('be.visible')
  .and('have.text', 'Submit')
  .and('not.be.disabled')
```


### 🧼 Summary Cheatsheet

```js
cy.get('.item').should('exist')
cy.get('input').should('have.value', 'Hello')
cy.get('.btn').should('have.class', 'active')
cy.get('.msg').should('contain', 'Success')
cy.get('.hidden').should('not.be.visible')

cy.get('.item').then($el => {
  expect($el.text()).to.include('Ramavtar')
})

```


---

# Hooks ->

Let’s gooo! 🎣 Time to master Hooks in Cypress — they make your tests cleaner, organized, and DRY (Don't Repeat Yourself).

### 🎯 1. What are Hooks?
Hooks in Cypress are special functions that run before or after your tests.
They're used for setup and teardown — like logging in, resetting a DB, or visiting a page.

Think of it like:

- "Before every test, go to the login page"
- "After all tests, log something"


### 🧪 2. The 4 Main Hooks

| Hook | When it Runs | Use Case | Example |
|------|--------------|----------|---------|
| `before()` | Once before all tests | Global setup | Login, seed test database |
| `beforeEach()` | Before every test case | Test preparation | Visit page, reset application state |
| `afterEach()` | After every test case | Cleanup | Take screenshot, clear cookies |
| `after()` | Once after all tests | Final teardown | Logout, generate reports |


### 🧠 3. Basic Examples

- Example 1 :
  
```js
describe('User Dashboard', () => {
  before(() => {
    cy.login('admin@test.com', 'password123') // Runs once
  })

  beforeEach(() => {
    cy.visit('/dashboard') // Runs before each test
  })

  afterEach(() => {
    cy.clearLocalStorage() // Runs after each test
  })

  after(() => {
    cy.logout() // Runs once at the end
  })

  it('should display welcome message', () => {
    // Test code...
  })
})
```


- Example 2 :

```js
describe('Login Flow', () => {

  before(() => {
    // Runs ONCE before all tests
    cy.log('🌟 Start Login Test Suite')
  })

  beforeEach(() => {
    // Runs BEFORE EACH test
    cy.visit('/login')
  })

  it('logs in with valid credentials', () => {
    cy.get('[data-cy="username-input"]').type('ramavtar')
    cy.get('[data-cy="password-input"]').type('123456')
    cy.get('[data-cy="submit-btn"]').click()
    cy.get('[data-cy="welcome-msg"]').should('contain', 'Welcome')
  })

  it('shows error on invalid login', () => {
    cy.get('[data-cy="username-input"]').type('wrong')
    cy.get('[data-cy="password-input"]').type('wrong')
    cy.get('[data-cy="submit-btn"]').click()
    cy.get('[data-cy="error-msg"]').should('be.visible')
  })

  afterEach(() => {
    // Runs AFTER EACH test
    cy.log('✅ One test completed')
  })

  after(() => {
    // Runs ONCE after all tests
    cy.log('🏁 All tests done')
  })

})
```


### 🔥 4. Pro Tips

- Use beforeEach() to visit the same page before each test.

- Avoid doing everything inside before() — use it only for one-time setups.

- Combine with fixtures, API calls, and custom commands for advanced setups.


### 💡 5. Summary Cheatsheet

```js
before(() => { /* once before all */ })
beforeEach(() => { /* before every test */ })
afterEach(() => { /* after every test */ })
after(() => { /* once after all */ })
```


---

# Custom Commands in Cypress ->

## 🛠️ What are Custom Commands ?

Custom commands let you create your own reusable Cypress functions — so you can avoid repeating code and keep your tests clean and readable.

Think of them like creating your own cy.login() or cy.fillForm() that works just like built-in commands like cy.get() or cy.visit().

### 🤔 1. Why Use Custom Commands?
- ✅ Reuse code across multiple tests
- ✅ Clean, readable, DRY (Don't Repeat Yourself) code
- ✅ Easier test maintenance
- ✅ Encapsulate logic (like login, signup, etc.)

### 📍 2. Where to Define Custom Commands ?

Inside:

```bash
cypress/support/commands.js
```

This file is automatically loaded by Cypress — no need to import it manually in each test file.


### 🧪 3. Example 1: Custom Login Command:

```js
// Inside cypress/support/commands.js

Cypress.Commands.add('login', (email, password) => {
  cy.visit('/login')
  cy.get('input[name="email"]').type(email)
  cy.get('input[name="password"]').type(password)
  cy.get('button[type="submit"]').click()
})
```


Then use it in your test like this:

```js
// Inside any test file
describe('Login Test', () => {
  it('logs in successfully', () => {
    cy.login('ramavtar@example.com', '123456')
    cy.url().should('include', '/dashboard')
  })
})
```

BOOM 💥 — no need to repeat all those cy.get().type() lines every time.



### 🧪 4. Example 2: Fill Signup Form

```js
// cypress/support/commands.js
Cypress.Commands.add('fillSignupForm', (name, email, password) => {
  cy.get('#name').type(name)
  cy.get('#email').type(email)
  cy.get('#password').type(password)
  cy.get('#signup-btn').click()
})
```


Usage:

```js
cy.fillSignupForm('Ramavtar', 'ram@example.com', 'pass123')
```

### 🔍 5. Best Practices

- ✅ Prefix command names with action verbs like cy.fill, cy.do, cy.perform
- ✅ Keep commands focused on one task
- ✅ Add comments to describe what your command does
- ✅ Use aliases if needed (e.g. cy.get('@userId'))

### 🧪 6. You Can Also Add Overwrites

You can even overwrite Cypress’s built-in commands (if needed):
Don't worry if you are not able to understand this ( we’ll see this in the next topics )

```js
Cypress.Commands.overwrite('visit', (originalFn, url, options) => {
  // Add auth headers to every visit if needed
  originalFn(url, {
    ...options,
    headers: { Authorization: 'Bearer my-token' },
  })
})
```

### ✅ 7. Recap: Custom Commands in Cypress

| Feature | Description | Example |
|---------|-------------|---------|
| `Cypress.Commands.add()` | Create your own custom command | `Cypress.Commands.add('login', (email, pw) => {...})` |
| **Place** | `cypress/support/commands.js` | Where all custom commands live |
| **Usage** | `cy.commandName(args)` | `cy.login('test@user.com', 'pass123')` |
| **Benefit** | Reusable, clean, DRY test code | Write once, use everywhere |

### 🧾 8. Custom Commands – Summary Cheatsheet

```js
// ✅ Define a custom command in cypress/support/commands.js
Cypress.Commands.add('login', (email, password) => {
  cy.get('#email').type(email)
  cy.get('#password').type(password)
  cy.get('form').submit()
})

// ✅ Use the custom command in your test
cy.login('ram@example.com', 'password123')
```

---

# 🛠️ Fixtures in Cypress ->

## 🔍 What are Fixtures?

Fixtures are external files (usually JSON, but can also be .txt, .csv, etc.) that contain test data. They help you separate test logic from test data, making your tests cleaner and easier to maintain.

### 📂 1. Where Do Fixtures Live ?
Cypress expects fixture files to be in the cypress/fixtures/ directory.

Example:
```pgsql
cypress/
  fixtures/
    user.json
```

### 📄 2. Example Fixture File: user.json

```json
{
  "name": "Avatar",
  "email": "avatar@example.com",
  "password": "password123"
}
```

### ✅ 3. How to Use Fixtures

You can load this data inside your test using the cy.fixture() command:

```js
describe('Using Fixtures', () => {
  it('logs in using fixture data', () => {
    cy.fixture('user').then((userData) => {
      cy.visit('/login');

      cy.get('#email').type(userData.email);
      cy.get('#password').type(userData.password);
      cy.get('form').submit();

      cy.contains('Welcome, Ram').should('be.visible');
    });
  });
});
```

### 🔁 4. Using Fixtures with Aliases
You can also alias the data for reuse:
Don't worry if you do not know about aliases ( we’ll see this in the next topics )

```js
beforeEach(() => {
  cy.fixture('user').as('user');
});

it('uses aliased fixture data', function () {
  cy.visit('/login');

  cy.get('#email').type(this.user.email);
  cy.get('#password').type(this.user.password);
  cy.get('form').submit();

  cy.contains(`Welcome, ${this.user.name}`).should('be.visible');
});
```

💡 Note the use of function() instead of arrow functions so this context is preserved.

### 🧠 5. Why Use Fixtures?

- Reusability: Share data across multiple tests.

- Maintainability: Update data in one place.

- Cleaner code: Keep tests focused on behavior, not data setup.


### 💡 6. Pro Tips

- Use JSON for structured data.

- Use .txt or .csv for raw content if needed.

- Combine fixtures with cy.intercept() to mock APIs ( we’ll see this in the next topics ).


### 🧾 7. Fixtures – Summary Cheatsheet

```js
// Load fixture data once inside a test
cy.fixture('fileName').then((data) => {
  // use data
})

// Load fixture and alias it
beforeEach(() => {
  cy.fixture('fileName').as('aliasName')
})

// Use alias (with function() to access this.aliasName)
it('uses fixture alias', function () {
  cy.get('selector').type(this.aliasName.key)
})

// Example fixture file: cypress/fixtures/user.json
/*
{
  "name": "Avatar",
  "email": "avatar@example.com",
  "password": "password123"
}
*/
```

---

# 🛠️ Aliases & .then() in Cypress ->

## 🔁 What Are Aliases?
Aliases in Cypress let you store values, elements, or fixture data for reuse later using @aliasName.
You create an alias using .as('name'), and access it with cy.get('@name').

### 📌 1. Common Alias Use Cases

- ✅ Aliasing DOM elements:
  ```js
    cy.get('input#email').as('emailInput')
    cy.get('@emailInput').type('ram@example.com')
  ```
  
- ✅ Aliasing fixture data:
  ```js
    cy.fixture('user').as('userData')
  
    it('uses alias for fixture', function () {
      cy.get('@userData').then((data) => {
        cy.get('#email').type(data.email)
      })
    })
  ```
- ✅ Aliasing intercepted API calls:
  ```js
  cy.intercept('GET', '/api/user').as('getUser')
  cy.wait('@getUser')
  ```

### ⏳ 3. .then() – Handling Async Data
.then() is a Cypress command used to work with resolved values from a previous command.

📌 Example:
```js
  cy.get('h1').then(($h1) => {
    const text = $h1.text()
    expect(text).to.equal('Welcome')
  })
```

Use .then() when:

- You need to extract a value

- You need to do custom logic

- You’re chaining async behavior

💡 Tip: .then() gives you direct access to the resolved subject.

### 🔀 4. Aliases + .then() = 💥

```js
  beforeEach(() => {
  cy.fixture('user').as('user')
})

it('logs in using aliased data', function () {
  cy.get('@user').then((user) => {
    cy.get('#email').type(user.email)
    cy.get('#password').type(user.password)
    cy.get('form').submit()
  })
})

```

### 🧾 5. Aliases & .then() – Summary Cheatsheet
```js
// Alias DOM elements
cy.get('selector').as('aliasName')
cy.get('@aliasName').type('value')

// Alias fixtures
cy.fixture('fileName').as('aliasName')
cy.get('@aliasName').then((data) => {
  // use data
})

// Alias network request
cy.intercept('GET', '/api/endpoint').as('alias')
cy.wait('@alias')

// .then() to handle resolved data
cy.get('selector').then(($el) => {
  const text = $el.text()
  expect(text).to.include('Hello')
})
```

---

# 🛠️ Environment Variables in Cypress

## 🔍 What are Environment Variables in Cypress?
They help keep your Cypress tests clean, flexible, and secure by separating configurable data from your test logic.

### 🎯 1. Why Use Them?

Environment variables allow you to store values like:

- Base URLs

- Credentials

- API keys

- Config flags (e.g. isProd, isMockEnabled)

So you don’t hardcode them directly in your tests.

### 📦 2. Defining Environment Variables

#### 1. 🔧 In cypress.config.js

```js
const { defineConfig } = require("cypress");

module.exports = defineConfig({
  env: {
    login_email: "ram@example.com",
    login_password: "password123"
  }
});
```

✅ Use cypress.config.js when:
- You want environment variables to be version-controlled.

- The variables are non-sensitive and part of the standard config (e.g., flags, test modes).

- You prefer having all config centralized.

***

#### 2. 📁 In cypress.env.json
Create a file in your root directory:

```json
{
  "login_email": "ram@example.com",
  "login_password": "password123"
}
```
🔒 This file is .gitignore-friendly for sensitive data.

✅ Use cypress.env.json when:
- You want to keep sensitive data out of version control (like credentials, API keys).

- You want to separate config from code — clean & secure.

- It’s ignored by default in .gitignore, so secrets stay safe.

***

### 🔍 3. Accessing Environment Variables
In Test Files:
```js
const email = Cypress.env('login_email')
const password = Cypress.env('login_password')

cy.get('#email').type(email)
cy.get('#password').type(password)
```

With Default Fallback:
```js
const mode = Cypress.env('mode') || 'development'
```

### 🚀 4. Passing Env Vars via CLI (for CI/CD)
```bash
npx cypress run --env login_email=ram@example.com,login_password=password123
```

### 👨‍💻 6. Use Case: Dynamic Login
```js
cy.visit('/login')
cy.get('#email').type(Cypress.env('login_email'))
cy.get('#password').type(Cypress.env('login_password'))
cy.get('form').submit()
```

### 🧾 7. Environment Variables – Summary Cheatsheet
```js
// Access env variable
Cypress.env('variableName')

// In cypress.config.js
env: {
  key: "value"
}

// In cypress.env.json
{
  "key": "value"
}

// From CLI
npx cypress run --env key=value

// With fallback
const val = Cypress.env('key') || 'defaultValue'
```

🔐 Best Practice:
Use cypress.env.json for secrets, and use cypress.config.js for public config flags or default values.

---

# 🌐 Network Requests – cy.intercept()

### 🧐 1. What is cy.intercept()?

cy.intercept() allows you to:

- Monitor network calls

- Stub/mock API responses

- Wait for requests before continuing

- Assert on request/response data

It replaced the old cy.route() and is way more powerful.

### 🔍 2. What’s the Goal?

- When your web app calls an API (like /api/login or /api/products), you might want to:

- See if the request is being made correctly

- Make your tests faster by avoiding real API calls

- Test how your app reacts to different server responses (success, error, empty data)

- Stop depending on a real server or live database to test

That’s what cy.intercept() is for.

### 🛠️ 3. Basic Syntax

```js
cy.intercept(method, url, routeHandler?)
```

- method: 'GET', 'POST', 'PUT', etc.

- url: exact string or pattern (/api/users, /api/*)

- routeHandler: (optional) to stub or modify the response


### 🔧 4. Think of cy.intercept() like a "traffic controller":

It lets you:

- Watch network calls 🚦  

- Change the response that your app receives 🛠️  

- Wait for a network call before moving forward ⏳  

## ✅ Let's Understand Each Use Case with Real-Life Style Examples: 

### 🧪 1. Just Watching a Request (no mocking)

Scenario: You visit a page and want to check if the frontend hits /api/users.

```js
cy.intercept('GET', '/api/users').as('getUsers') // watch the request
cy.visit('/dashboard') // page loads and triggers the call
cy.wait('@getUsers') // wait until the request is made
```

📌 Use this when you want to wait for the request to finish or assert it was called.


### 🧪 2. Mocking the Response (fake data)

Scenario: You want to skip the actual backend and return fake data.

```js
cy.intercept('GET', '/api/users', {
  statusCode: 200,
  body: [{ id: 1, name: 'Ram' }]
}).as('mockUsers')
```

📌 This will make Cypress return this fake data when your app calls /api/users.

⭐ Great for testing the UI when:

-  You don’t want to depend on the backend

-  The backend is not ready yet

-  You want consistent data in tests

### 🧪 3. Using a JSON Fixture File as a Response

Scenario: You have a file users.json with sample users inside cypress/fixtures.

```json
// cypress/fixtures/users.json
[
  { "id": 1, "name": "Ram" },
  { "id": 2, "name": "Shyam" }
]
```

⭐ Then in your test:

```js
cy.intercept('GET', '/api/users', { fixture: 'users.json' }).as('usersList')
```

📌 Easier to manage large or reusable mock data.

### 🧪 4. Intercepting POST Requests & Checking Data Sent

Scenario: You want to test login. Make sure your app sends the correct email/password and gets a token back.

```js
cy.intercept('POST', '/api/login', (req) => {
  expect(req.body.email).to.equal('ram@example.com')
  req.reply({
    statusCode: 200,
    body: { token: 'abc123' }
  })
}).as('loginRequest')
```

📌 This:

- Verifies the frontend is sending the right data

- Gives a fake login success response to move test forward

### 🧪 5. Wait for Request + Check the Response

After your app sends a request, you can wait() and then check the result:

```js
cy.wait('@loginRequest').then((interception) => {
  expect(interception.response.statusCode).to.eq(200)
  expect(interception.response.body.token).to.exist
})
```

📌 Useful to confirm:

- The server responded correctly

- The app handled it properly

### ✅ 6. Common Real-World Use Cases

| Use Case                     | What to Do                                           |
|-----------------------------|------------------------------------------------------|
| Wait for backend data to load | `cy.intercept()` + `cy.wait()`                     |
| Fake login/logout flows      | Intercept `POST /login` and return a mock token     |
| Test empty list / errors     | Intercept and send `{}` or a `500` error            |
| Avoid real API calls in CI   | Intercept all APIs and return stubbed responses     |


### 🧾 7. Cheatsheet – Network Requests Summary

```js
// Just watch a request (no mock)
cy.intercept('GET', '/api/data').as('apiData')
cy.wait('@apiData')

// Mock a response (inline)
cy.intercept('GET', '/api/data', {
  statusCode: 200,
  body: { message: 'Mocked data here' }
}).as('mockData')


// Use fixture file
cy.intercept('GET', '/api/data', { fixture: 'data.json' }).as('fixtureData')

// Intercept POST and validate request
cy.intercept('POST', '/api/login', (req) => {
  expect(req.body.email).to.eq('ram@example.com')
  req.reply({ statusCode: 200, body: { token: 'xyz' } })
}).as('login')

// Wait + check the response
cy.wait('@login').then((interception) => {
  expect(interception.response.statusCode).to.eq(200)
})
```


