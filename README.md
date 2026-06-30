# Unit Testing – Java Application

## Team Members

- Full Name: avia lurie (ID: 315150516)
- Full Name: Yuval Arvili (ID: 214630089)

---

## Prerequisites

Before cloning and running the project, make sure the following are installed on your machine:

| Tool | Minimum Version | Download |
|---|---|---|
| Git | Any | https://git-scm.com |
| Java JDK | 21 | https://adoptium.net |

> You do **not** need to install Gradle manually — the project includes a Gradle Wrapper (`gradlew`) that downloads the correct version automatically.

---

## Step 1 — Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/Afeka-DevTools/26b-10142-unittesting-yuval-avia.git
```

Then navigate into the project folder:

```bash
cd 26b-10142-unittesting-yuval-avia
```

---

## Step 2 — Verify Java is Installed

```bash
java -version
```

Expected output (version 21 or higher):

```
openjdk version "21.x.x" ...
```

---

## Step 3 — Run All Tests

**On macOS / Linux:**

```bash
./gradlew test
```

**On Windows:**

```bat
gradlew.bat test
```

Gradle will automatically download all dependencies and run the 45 unit tests.

---

## Step 4 — View the Test Report

After the tests finish, open the HTML report in your browser:

**On macOS / Linux:**

```bash
open app/build/reports/tests/test/index.html
```

**On Windows:**

```bat
start app\build\reports\tests\test\index.html
```

The report shows each test method, its result (pass/fail), and execution time.

---

## Step 5 — Run Tests with Coverage Report (JaCoCo)

To run the tests and generate a code coverage report:

**On macOS / Linux:**

```bash
./gradlew test jacocoTestReport jacocoTestCoverageVerification
```

**On Windows:**

```bat
gradlew.bat test jacocoTestReport jacocoTestCoverageVerification
```

Then open the coverage report:

**On macOS / Linux:**

```bash
open app/build/reports/jacoco/test/html/index.html
```

**On Windows:**

```bat
start app\build\reports\jacoco\test\html\index.html
```

> The build is configured to **fail** if coverage drops below **80%**.

---

## Project Structure

```
26b-10142-unittesting-yuval-avia/
├── app/
│   ├── src/
│   │   ├── main/java/org/example/
│   │   │   └── App.java          ← source code (11 utility methods)
│   │   └── test/java/org/example/
│   │       └── AppTest.java      ← 45 unit tests (all edge cases covered)
│   └── build.gradle.kts          ← build config with JaCoCo (min 80% coverage)
├── logs/
│   ├── LEARNING.md               ← LLM conversation: learning about unit testing
│   └── COPILOT.md                ← LLM conversation: writing the tests with Claude Code
├── gradlew                       ← Gradle Wrapper (Linux/Mac)
├── gradlew.bat                   ← Gradle Wrapper (Windows)
└── README.md
```

---

## Test Summary

| Method | Tests |
|---|---|
| `add` | 4 |
| `isPrime` | 3 |
| `reverse` | 3 |
| `factorial` | 3 |
| `isPalindrome` | 5 |
| `fibonacciUpTo` | 4 |
| `charFrequency` | 3 |
| `isAnagram` | 6 |
| `average` | 5 |
| `filterEvens` | 5 |
| `mostCommonWord` | 4 |
| **Total** | **45** |
