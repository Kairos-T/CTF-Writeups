# SQL Injection

Lab Writeups:

1. [Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](sql-injection.md#1.-lab-sql-injection-vulnerability-in-where-clause-allowing-retrieval-of-hidden-data)
2. [Lab: SQL injection vulnerability allowing login bypass](sql-injection.md#2.-lab-sql-injection-vulnerability-allowing-login-bypass)



## 1. Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data











## 2. Lab: SQL injection vulnerability allowing login bypass

The website had a login page, so I tried using random credentials to see if the error message would indicate anything, which it wasn't very helpful.

<figure><img src="../../.gitbook/assets/Screenshot from 2023-08-28 18-12-37.png" alt=""><figcaption></figcaption></figure>

Moving on, I tried to add a `'` character to mess up the query.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2023-08-28 18-12-42.png" alt=""><figcaption></figcaption></figure>

I was brought to an internal server error page which showed that there wasn't enough input filtering/validation which caused an error at the backend.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2023-08-28 18-12-51.png" alt=""><figcaption></figcaption></figure>

Knowing this, I entered `administrator'--` to make the rest of the query to be intepreted as a comment, removing the remainder of the query.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2023-08-28 18-13-07.png" alt=""><figcaption></figcaption></figure>

And this made it simple to solve the lab!

<figure><img src="../../.gitbook/assets/Screenshot from 2023-08-28 18-11-53.png" alt=""><figcaption></figcaption></figure>



