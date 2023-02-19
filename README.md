# Micro-CMS-v2-Blind-SQLi

I. Introduction

        Blind SQL injection (SQLi) is a type of SQL injection attack where an attacker can infer the content of the
    database without directly extracting the data. This is achieved by sending crafted SQL queries to the
    application and analyzing the response of the server, without actually seeing the database content. Blind SQLi
    is commonly used in CTF (Capture the Flag) challenges as a way to test the ability of participants to exploit
    vulnerabilities in web applications. By exploiting Blind SQLi, participants can demonstrate their skills in 
    finding and exploiting vulnerabilities, as well as their ability to analyze application behavior and logic to
    infer the content of the database. Blind SQLi challenges can vary in complexity and difficulty, ranging from
    basic Boolean-based techniques to more advanced techniques involving time delays, error messages, and other
    indicators.

II. Information Gathering

        After spinning up burp and enabling the proxy I loaded into the website and noticed a CMS changelog link.
    Upon viewing the page I can see they added a login page as well as a change that allows only admins to edit
    and add pages. Continuing mapping the application I click the Markdown Test and notice its similar to CMSv1
    but whenever you try to edit that page is directs you to a login page /admin. The last link is the Create a
    new page which also redirects you to the /admin page. With all of these POST/GET requests in Burp we can start
    to see these interactions in more detail. This concludes the mapping of the application for now.
           

III. Exploitation

        Now that the application has been mapped with all of its functionality I start to fuzz my attack surface.
    I started with the login page as that would open up the most functionality to us. I started by inputting some 
    common username/passwords and notice I get an Unknown User error. None of the easy gimmies worked like
    admin/password...etc. Onto special characters for SQL considering it is a login page and would you look at that. 
    A single apostrophe has done the job. We get an error with the exact SQL query being placed into the backend as
    well as which DB is in use, which is MariaDB. Now I know that I can escape it and write my own magic! I start    
    small and build up... 
    
    **Testing Boolean Payloads:**
    ~~~
    payload1: ' OR (1=1)# // Well that's nice, no errors and it ALSO displays a new error "Invalid Password"
    
    Payload2: ' OR (SELECT CASE WHEN (1=1) THEN 1=1 ELSE 1=2 END)# // Changing the conditionals works
    ~~~
    **Enumeration Test:**
    ~~~
    Payload3: ' OR (SELECT CASE WHEN SUBSTRING(@@version,1,1)='1' THEN 1=1 ELSE 1=2 END)# //Enumerates DB version
    ~~~
    **Enumerating Length of the 1st username**
    ~~~
    Payload4: ' OR LENGTH(username)=5# // Enums length of username
   
    Payload5: ' OR LENGTH(password)=5# // Enums length of password
    ~~~
    
    
    
    
    
    You can also try UNION SELECT but I decided to stick with boolean payloads as they are my favorite.
    ```
    Payload: ' OR (UNION SELECT NULL#) // This also doesn't give us an error but adding a second NULL value errors   
    
    ```
    

    
    
    
    
    
    
    

IV. Flag Retrieval

    Determine the structure of the database and the relevant tables/columns that might contain the flag
    Use SQL commands to extract the flag value
    Double-check that you've extracted the correct flag value

V. Conclusion

    Summarize the steps taken to successfully complete the Blind SQLi challenge
    Reflect on the skills and tools used and what could be improved in future challenges.
