# Log Book 8

## Task 1
For this task we want to display the information of the employee 'Alice'. We achieved this using the following query:

![](imgs/week8/task1.png)


## Task 2
SQL injection is basically a technique through which attackers can execute their own malicious SQL statements generally referred as malicious payload. Through the malicious SQL statements, attackers can steal information from the victim database or even worse they may be able to make changes to the database. Our employee management web application has SQL injection vulnerabilities, which mimic the mistakes frequently made by developers.

### Task 2.1
Log in into the web application as the administrator from the login page, so that you can see the information of all employees. Exploiting the php query vulnerability.

![](imgs/week8/logbook8_task2.1_1.png)

The single quote after entering a valid username existing in the database, closes the argument for the input username and the \# sign consequently makes everything after the username to be commented out.

![](imgs/week8/logbook8_task2.1_2.png) 

Hence, we were able to get all the information about the employees using the admin ID.

### Task 2.2
Repeat Task 2.1 but from the command line using curl. We use the curl command to place an HTTP request to the webapplication and perform the login from the command line.

![](imgs/week8/logbook8_task2.2_1.png)

For the username we need to pass **admin'\#** which are special caracters, and therefore need to be enconded. We used the following encodings **Quote (') -> %27** and **Hash (\#) -> %23**.

![](imgs/week8/logbook8_task2.2_2.png)

### Task 2.3
There is a countermeasure preventing you from running two SQL statements in this attack. Please use the SEED book or resources from the Internet to figure out what this countermeasure is, and describe your discovery in the lab report.

![](imgs/week8/logbook8_task2.3_1.png)

This SQL injection does not work in MySQL because PHP's mysqli extension, mysqli::query() API does not allow multiple queries to run in the databse server. The limitation is inserted by the extension not the SQL server itself. This mysqli limitation can be overcome by using mysqli->multiquery().

## Task 3
If a SQL injection vulnerability happens to an UPDATE statement, the damage will be more severe, because attackers can use the vulnerability to modify databases. In our Employee Management application, there is an Edit Profile page (Figure 2) that allows employees to update their profile information, including nickname, email, address, phone number, and password. To go to this page, employees need to log in first.

### Task 3.1
##### Modify your own salary.

![](imgs/week8/logbook8_task3.1_1.png) 
![](imgs/week8/logbook8_task3.1_2.png) 

To modify Alice's salary we used the NickName text box to run the specific MySQL command : ', Salary='999999' WHERE Name="Alice"#.

### Task 3.2
##### Modify other people’ salary.

![](imgs/week8/logbook8_task3.2_2.png)
![](imgs/week8/logbook8_task3.2_1.png)

To modify Boby's salary we used the NickName text box to run the specific MySQL command : ', Salary='1' WHERE Name="Boby"#.

### Task 3.3
##### Modify other people’ password.

![](imgs/week8/logbook8_task3.3_1.png)

To modify Boby's password we used the Address text box to run the specific MySQL command : ',Password=sha1('123') WHERE Name="Boby"#.

![](imgs/week8/logbook8_task3.3_2.png)
![](imgs/week8/logbook8_task3.3_3.png)

Then we used that password to login as Boby -> username: Boby | password: 123

---

## CTF 8

### Challenge 1

This CTF is all about SQL Injection, where we are given a login page, and we have to try to login as **admin**. We tried the same SQL Injection type query as in task 2 `admin'--` and we had to write a random character in the password text box as it seems it can not be null.
![](imgs/week8/logbook8_ctf8_1.png)
![](imgs/week8/logbook8_ctf8_2.png)

### Challenge 2

In this challenge we had to create an exploit that uses a shell in the server to obtain the flag present in the program's working directory.

![](imgs/week8/ctf8challenge2-1.png)

As we can see PIE is enabled so there is address space randomization which means that the addresses change everytime the program is executed. However, when running the program the buffer address is given.

The vulnerability in this challenge is a buffer overflow. A buffer for 100 characters is created but using the gets function it is possible to insert the number of characters that the user wants. This vulnerability is found on line 12.

Knowing this, we made an exploit, which first obtains the address of the buffer and then creates the payload to execute the Buffer Overflow.

![](imgs/week8/ctf8challenge2-2.png)
