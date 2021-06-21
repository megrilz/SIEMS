# SIEMS

# Scenario
Design mitigation strategies to protect VSI from future attacks.
You are tasked with using your findings from the Master of SOC activity to answer questions about mitigation strategies.
System Requirements
I used the Splunk app located in the Ubuntu VM.
Logs
Windows Logs
Windows Attack Logs
Apache Webserver Logs
Apache Webserver Attack Logs

# Part 1: Windows Server Attack
This is a public-facing windows server that VSI employees access.
# Question 1
Several users were impacted during the attack on March 25th.
Based on the attack signatures, what mitigations would you recommend to protect each user account? Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.

![image](https://user-images.githubusercontent.com/80080368/122814015-a3867e00-d2a1-11eb-90b4-2de3340342fb.png)


# Individual level
Educate your employees and conduct training sessions with mock phishing scenarios.
Limit account lockouts to 3 times an hour and escalate the time if the user continues to get locked out
Enable two factor authentication to reset your password
Prohibit users from resetting their passwords to only once every 2 days. To contact the tech department if you need your password reset. Reset the password by sending the user an encrypted password.
# Global level
Deploy a SPAM filter that detects viruses, blank senders, etc.
Keep all systems current with the latest security patches and updates.
Install an antivirus solution, schedule signature updates, and monitor the antivirus status on all equipment.
Develop a security policy that includes but isn't limited to password expiration and complexity.
Deploy a web filter to block malicious websites.
Encrypt all sensitive company information.
Convert HTML email into text only email messages or disable HTML email messages.

# Question 2
VSI has insider information that JobeCorp attempted to target users by sending "Bad Logins" to lock out every user.
What sort of mitigation could you use to protect against this?
Limit forgotten password policy, must answer security questions first or pass a 2 factor authentication. Encrypt the cookies and do not enable the remember me function for users to store their data. To prevent information leakage leading to username enumeration, the application should never indicate that any specific account has been suspended. Rather, it should respond to any series of failed logins, even those using an invalid username, with a message advising that accounts are suspended if multiple failures occur and that the user should try again later.

![image](https://user-images.githubusercontent.com/80080368/122814081-bb5e0200-d2a1-11eb-8a8f-b2d9623655ce.png)



# Part 2: Apache Webserver Attack:
# Question 1
Based on the geographic map, recommend a firewall rule that the networking team should implement.


Block all incoming HTTP traffic where the source IP comes from the city of Paris.
Provide a screen shot of the geographic map that justifies why you created this rule.

![image](https://user-images.githubusercontent.com/80080368/122814340-0b3cc900-d2a2-11eb-82d7-81930d84a0d1.png)





# Question 2
VSI has insider information that JobeCorp will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule you just created.


What other rules can you create to protect VSI from attacks against your webserver?


Use UBA and determine the usual IPs and geographic locations each user connects from to follow those trends. Any outliers should not be given access. Create alerts from unusual activity like log in hours. 


![image](https://user-images.githubusercontent.com/80080368/122814416-260f3d80-d2a2-11eb-836c-c505e5544497.png)


Block all incoming HTTP with a byte size over 65,748.This is above average for traffic. 

![image](https://user-images.githubusercontent.com/80080368/122814455-31626900-d2a2-11eb-8432-65f80ac7a8e5.png)



Block all incoming HTTP traffic where useragent us "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.2; SV1; .NET CLR 2.0.50727987787; InfoPath.1)"
