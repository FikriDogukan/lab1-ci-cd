# Lab 1: CI/CD Pipeline Implementation

## 📌 Objective
This lab focuses on implementing a Continuous Integration and Continuous Deployment (CI/CD) pipeline for an application. The goal is to automate the build, test, and deployment processes to enhance software development efficiency and reliability.

## 🎯 Expected Outcomes
By the end of this lab, you will have:
- Set up a CI/CD pipeline using GitHub Actions or another CI/CD tool.
- Automated the build and testing of an application.
- Configured deployment to a chosen environment.
- Improved development workflow through automation.

## 🛠 Prerequisites
Before starting, ensure you have the following:
- A GitHub repository with your application code.
- Basic understanding of version control with Git.
- Familiarity with GitHub Actions or another CI/CD service.
- A deployment target (e.g., Heroku, Vercel, AWS, or a server).

## 🚀 Steps to Implement CI/CD

### 1️⃣ Step 1: Set Up the GitHub Repository
1. Clone the repository:
   ```sh
   git clone https://github.com/FikriDogukan/lab1-ci-cd.git
   cd lab1-ci-cd
   ```
2. Ensure your project contains a `package.json` (for Node.js) or equivalent build configuration file.

### 2️⃣ Step 2: Define the CI/CD Workflow
1. Navigate to the `.github/workflows/` directory (create it if it does not exist).
2. Create a YAML file for GitHub Actions:
   ```sh
   mkdir -p .github/workflows
   touch .github/workflows/ci-cd.yml
   ```
3. Add the following example configuration for a **Node.js** project:
   ```yaml
   name: CI/CD Pipeline

   on:
     push:
       branches:
         - main
     pull_request:
       branches:
         - main

   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout Repository
           uses: actions/checkout@v2

         - name: Setup Node.js
           uses: actions/setup-node@v2
           with:
             node-version: '16'

         - name: Install Dependencies
           run: npm install

         - name: Run Tests
           run: npm test

         - name: Build Application
           run: npm run build

         - name: Deploy
           run: echo "Deployment step (replace with actual deployment commands)"
   ```
4. Commit and push the workflow file:
   ```sh
   git add .
   git commit -m "Added CI/CD workflow"
   git push origin main
   ```

### 3️⃣ Step 3: Monitor Workflow Execution
1. Go to your GitHub repository.
2. Navigate to **Actions** to see the workflow execution.
3. If there are errors, debug based on the logs.

### 4️⃣ Step 4: Configure Deployment
Depending on your deployment target, modify the `Deploy` step in the CI/CD workflow.
- **For Heroku**:
  ```yaml
  - name: Deploy to Heroku
    uses: akhileshns/heroku-deploy@v3.12.12
    with:
      heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
      heroku_app_name: "your-heroku-app-name"
      heroku_email: "your-email@example.com"
  ```
- **For Vercel**:
  ```yaml
  - name: Deploy to Vercel
    run: npx vercel --prod --token ${{ secrets.VERCEL_TOKEN }}
  ```

## 📊 Monitoring & Maintenance
- Regularly check the **Actions** tab for workflow status.
- Update dependencies and security patches frequently.
- Implement proper logging and monitoring.

## ❓ Questions & Troubleshooting
If you face any issues:
1. Check workflow logs under the **Actions** tab.
2. Validate environment variables and API keys.
3. Verify `package.json` scripts for build/test issues.
4. Seek help from CI/CD documentation or forums.

## 📜 Conclusion
This lab demonstrates the fundamental concepts of setting up a CI/CD pipeline. By integrating automation into your development workflow, you ensure a seamless, error-free deployment process while improving code quality and reliability. 🚀

---

🔗 **GitHub Repository:** [lab1-ci-cd](https://github.com/FikriDogukan/lab1-ci-cd)

📩 For questions, feel free to reach out!

