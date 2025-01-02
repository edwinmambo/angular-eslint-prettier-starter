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

### Step 1: Clone the Repository 🐙

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
           "parser": "html"
         }
       },
       {
         "files": "*.component.html",
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

## 🎉 Conclusion

This project template provides a solid foundation for Angular applications with ESLint and Prettier integrated. It ensures consistent code quality and formatting across your project, following best practices for modern Angular development.

Feel free to customize the ESLint and Prettier configurations to suit your specific needs and preferences. Happy coding! 🚀
