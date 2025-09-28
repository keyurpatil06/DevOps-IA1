# DevOps-IA1 – Continuous Testing with Selenium IDE and Jenkins Pipeline

## 📌 Project Overview
This project demonstrates the use of **Selenium IDE** as an alternative tool for the **Continuous Testing** stage of the DevOps lifecycle.  
The recorded test cases are integrated into a **Jenkins pipeline** using `selenium-side-runner`, enabling automated browser-based testing within a CI/CD workflow.

---

## ⚙️ Tools & Technologies
- **Selenium IDE (Firefox extension)** – Record & playback test automation.
- **Selenium-Side-Runner (Node.js CLI)** – Executes `.side` test cases in CI/CD.
- **Geckodriver + Firefox** – Required for running recorded tests.
- **Jenkins** – Automates pipeline stages and integrates testing into DevOps.
- **Node.js + npm** – Package manager to install dependencies.

## 🛠️ Setup Instructions

### 1. Local Setup
1. Install [Node.js](https://nodejs.org/).
2. Install [Firefox Browser](https://www.mozilla.org/en-US/firefox/new/).
3. Download [Geckodriver](https://github.com/mozilla/geckodriver/releases) and:
   - Extract it.
   - Place `geckodriver.exe` in `C:\Windows\System32` or add its folder to PATH.
4. Clone this repository:
   ```bash
   git clone https://github.com/keyurpatil06/DevOps-IA1.git
   cd DevOps-IA1
5. Run the Selenium IDE test locally:
    - Open the .side file (Keyur_DEVOPS_IA.side) in Selenium IDE Firefox extension.
    - Play the test to see automation steps execute on the browser.
    - Also can run in headless mode to simulate CI/CD testing without opening a visible browser window.

### 2. Jenkins Pipeline

1. Install Jenkins and configure it with Node.js and Firefox/Geckodriver.
2. Create a Pipeline job in Jenkins and link it to this GitHub repository.
3. Jenkins will automatically run the Selenium IDE test:
    - Cloning the repository
    - Installing dependencies
    - Executing the .side test in a headless browser
4. Check the Jenkins Console Output to view test execution results, including which steps passed or failed