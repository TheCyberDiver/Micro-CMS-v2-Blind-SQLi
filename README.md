# Micro-CMS-v2-Blind-SQLi

I. Introduction

    Briefly explain what Blind SQLi is and why it's used in CTF challenges
    Introduce the specific Blind SQLi challenge and the objective (finding a single flag)

II. Information Gathering

    Identify the target website and its functionality
    Use a web proxy like Burp Suite to intercept and analyze HTTP requests and responses
    Look for vulnerabilities and input fields where you can inject SQL commands
    Use SQLMap or a similar tool to automate some of the testing

III. Exploitation

    Test for SQL injection vulnerabilities by injecting various SQL commands into input fields
    Observe the website's behavior and use different techniques to confirm whether SQL injection is possible (e.g. Boolean-based, time-based, error-based)
    If successful, craft an exploit to extract the flag by injecting SQL commands to retrieve data

IV. Flag Retrieval

    Determine the structure of the database and the relevant tables/columns that might contain the flag
    Use SQL commands to extract the flag value
    Double-check that you've extracted the correct flag value

V. Conclusion

    Summarize the steps taken to successfully complete the Blind SQLi challenge
    Reflect on the skills and tools used and what could be improved in future challenges.
