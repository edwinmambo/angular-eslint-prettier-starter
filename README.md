# 🌟 Angular ESLint + Prettier Starter

## 📖 Overview

This project is a starter template for Angular applications with **ESLint** and **Prettier** integrated. It ensures consistent code quality and formatting across your project, following best practices for modern Angular development.

## ✨ Features

- 🛠️ **ESLint**: Linting for TypeScript and Angular-specific files.
- 🎨 **Prettier**: Automatic code formatting for consistent style.
- 🎨 **SCSS Support**: Configured to lint SCSS files in addition to TypeScript and HTML.

## 🧰 Software and Tools

This project template is built using the following tools and their major versions:

- **Angular**: Version `19.0.5`
- **Angular CLI**: Version `19.0.6`
- **Node.js**: Version `22.12.0`
- **Yarn**: Version `1.22.22`
- **TypeScript**: Version `5.6.3`
- **ESLint**: Version `9.17.0`
- **Prettier**: Version `3.4.2`
- **@angular-eslint**: Version `19.0.2`

## 🚀 Setup Instructions (How to Use the Template)

### 1️⃣Step 1: Clone the Repository 🐙

```bash
git clone git@github.com:edwinmambo/angular-eslint-prettier-starter.git
```

### Step 2: Install Dependencies 📦

Run the following command to navigate to the project directory:

```bash
cd angular-eslint-prettier-starter
```

Install all required dependencies using Yarn:

```bash
yarn install
```

### Step 3: Format Code 🎯

Use the following command to format your codebase:

```bash
yarn format
```

To automatically fix formatting issues with Prettier, run the following command:

```bash
yarn format:fix
```

### Step 4: Run Linting ✅

Use the following command to check your project for linting issues:

```bash
yarn lint
```

To automatically fix linting issues, run the following command:

```bash
yarn lint:fix
```

### Step 5: Start the Application 🌐

Run the following command to start the Angular application:

```bash
yarn start
```

Navigate to `http://localhost:4200/` in your browser to view the application.

## 🔧 How This Template Was Made

### **Step 1: Create an Angular Project**

1. Run the Angular CLI command to create a new project:

   ```bash
   ng new angular-eslint-prettier-starter --style=scss --routing
   ```

   - Selected **SCSS** as the default style format.

2. Navigate to the project directory:
   ```bash
   cd angular-eslint-prettier-starter
   ```

### **Step 2: Add ESLint**

1. Install Angular ESLint using the CLI:

   ```bash
   ng add @angular-eslint/schematics
   ```

2. Update the `angular.json` file to include the `@angular-eslint/builder:lint`:

   ```json
   "lint": {
     "builder": "@angular-eslint/builder:lint",
     "options": {
       "lintFilePatterns": [
         "src/**/*.ts",
         "src/**/*.html",
         "src/**/*.scss"
       ]
     }
   }
   ```

3. Add rules for Angular component and directive selectors in the `.eslintrc` file:

   ```json
   {
     "parserOptions": {
       "project": "./tsconfig.json"
     },
     "plugins": ["prettier"],
     "overrides": [
       {
         "files": ["**/*.ts"],
         "extends": [
           "eslint:recommended",
           "plugin:@typescript-eslint/recommended",
           "plugin:@typescript-eslint/stylistic",
           "plugin:@angular-eslint/recommended",
           "plugin:prettier/recommended"
         ],
         "rules": {
           "@angular-eslint/directive-selector": [
             "error",
             {
               "type": "attribute",
               "prefix": "app",
               "style": "camelCase"
             }
           ],
           "@angular-eslint/component-selector": [
             "error",
             {
               "type": "element",
               "prefix": "app",
               "style": "kebab-case"
             }
           ]
         }
       },
       {
         "files": ["**/*.html"],
         "extends": [
           "plugin:@angular-eslint/template/recommended",
           "plugin:@angular-eslint/template/accessibility"
         ],
         "rules": {
           "prettier/prettier": "error"
         }
       }
     ]
   }
   ```

### **Step 3: Add Prettier**

1. Install Prettier and related ESLint plugins:

   ```bash
   yarn add --dev prettier eslint-plugin-prettier eslint-config-prettier
   ```

2. Create a `.prettierrc` file to configure Prettier:

   ```json
   {
     "tabWidth": 2,
     "useTabs": false,
     "singleQuote": true,
     "semi": true,
     "bracketSpacing": true,
     "arrowParens": "avoid",
     "trailingComma": "es5",
     "bracketSameLine": true,
     "printWidth": 80,
     "endOfLine": "auto",
     "overrides": [
       {
         "files": "*.html",
         "options": {
           "parser": "angular"
         }
       }
     ]
   }
   ```

3. Create a `.prettierignore` file to exclude specific files and directories:

   ```plaintext
   node_modules/
   dist/
   coverage/
   .angular/
   ```

### **Step 4: Add a Format Script**

1. Add a `format` script to the `package.json` file:

   ```json
   "scripts": {
     "lint": "ng lint",
     "lint:fix": "ng lint --fix",
     "format": "prettier --check \"src/**/*.{ts,html,scss,json}\"",
     "format:fix": "prettier --write \"src/**/*.{ts,html,scss,json}\""
   }
   ```

### **Step 5: Run Linting and Formatting**

1. Run the linting script to check for issues:

   ```bash
   yarn lint
   ```

2. Run the formatting script to ensure consistent code style:

   ```bash
   yarn format
   ```

## 🛠️ Integrating Husky, lint-staged, and Commitlint

To ensure high-quality commits and enforce code standards, you can integrate **Husky**, **lint-staged**, and **Commitlint** into your project. These tools help automate linting, formatting, and commit message validation.

### Step 1: Install Dependencies

Install the required packages for Husky, lint-staged, and Commitlint:

```bash
yarn add --dev husky lint-staged @commitlint/cli @commitlint/config-conventional
```

### Step 2: Initialize Husky 🐾

Run the following command to initialize Husky in your project:

```bash
npx husky init
```

This will set up a `.husky` directory and create a default pre-commit hook.

### Step 3: Configure lint-staged 🧹

Update your `package.json` file to include the `lint-staged` configuration:

```json
  "lint-staged": {
    "*.{ts,scss,html}": [
      "eslint --fix",
      "prettier --check"
    ]
  },
```

This configuration ensures that only staged files are linted and formatted.

### Step 4: Add a Pre-Commit Hook 🔒

Modify the Husky pre-commit hook to use lint-staged. Open `.husky/pre-commit` and replace its contents with:

```bash
# .husky/pre-commit

npx lint-staged
```

### Step 5: Set Up Commitlint 📝

1. Create a `.commitlintrc` configuration file in the root of your project:

   ```json
   {
     "extends": ["@commitlint/config-conventional"]
   }
   ```

2. Add a Husky commit-msg hook to validate commit messages. Create a `.husky/commit-msg` file with the following content:

   ```bash
   # .husky/commit-msg

   npx --no-install commitlint --edit "$1"
   ```

### Step 6: Test the Setup 🧪

1. Make changes to a file in your project and stage it using `git add`.
2. Attempt to commit your changes with an invalid commit message. For example:

   ```bash
   git commit -m "fixing stuff"
   ```

You should see an error because the message doesn't follow the Conventional Commits format.

3. Use a valid commit message format like this:

   ```bash
   git commit -m "fix: resolve linting issues in AppComponent"
   ```

## Important Note: ESLint Configuration Update

If you are currently using `.eslintrc` and encounter compatibility issues, run the following command:

```bash
export ESLINT_USE_FLAT_CONFIG=false
```

Likewise, consider migrating to ESLint's flat configuration. You can do this by creating an `eslint.config.js` file with the following content:

```javascript
// @ts-check
const eslint = require('@eslint/js');
const tseslint = require('typescript-eslint');
const angular = require('angular-eslint');
const eslintPluginPrettierRecommended = require('eslint-plugin-prettier/recommended');

module.exports = tseslint.config(
  {
    files: ['**/*.ts'],
    extends: [
      eslint.configs.recommended,
      ...tseslint.configs.recommended,
      ...tseslint.configs.stylistic,
      ...angular.configs.tsRecommended,
      eslintPluginPrettierRecommended,
    ],
    processor: angular.processInlineTemplates,
    rules: {
      '@angular-eslint/directive-selector': [
        'error',
        {
          type: 'attribute',
          prefix: 'app',
          style: 'camelCase',
        },
      ],
      '@angular-eslint/component-selector': [
        'error',
        {
          type: 'element',
          prefix: 'app',
          style: 'kebab-case',
        },
      ],
    },
  },
  {
    files: ['**/*.html'],
    extends: [
      ...angular.configs.templateRecommended,
      ...angular.configs.templateAccessibility,
    ],
    rules: {},
  }
);
```

### Commit Message Format

Follow the Conventional Commits format for your commit messages:

- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation updates
- **style**: Code style changes (e.g., formatting)
- **refactor**: Code restructuring without feature or bug changes
- **test**: Adding or updating tests
- **chore**: Maintenance tasks (e.g., updating dependencies)

Example:

```bash
feat: add user authentication feature
```

### 🎉 You're All Set!

With **Husky**, **lint-staged**, and **Commitlint** integrated, your project now has robust pre-commit and commit message validation, ensuring code quality and team collaboration standards. 🚀

## 🎉 Conclusion

This project template provides a solid foundation for Angular applications with ESLint and Prettier integrated. It ensures consistent code quality and formatting across your project, following best practices for modern Angular development.

Feel free to customize the ESLint and Prettier configurations to suit your specific needs and preferences. Happy coding! 💻🎨
