# Micro-CMS-v2-Blind-SQLi

I. Introduction

    Blind SQL injection (SQLi) is a type of SQL injection attack where an attacker can infer the content of the    database without directly extracting the data. This is achieved by sending crafted SQL queries to the application and analyzing the response of the server, without actually seeing the database content. Blind SQLi is commonly used in CTF (Capture the Flag) challenges as a way to test the ability of participants to exploit vulnerabilities in web applications. By exploiting Blind SQLi, participants can demonstrate their skills in finding and exploiting vulnerabilities, as well as their ability to analyze application behavior and logic to infer the content of the database. Blind SQLi challenges can vary in complexity and difficulty, ranging from basic Boolean-based techniques to more advanced techniques involving time delays, error messages, and other indicators.
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
