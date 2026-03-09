# Snapped Phishing-Line Step by Step Documentation and Answers

### 1) Who is the individual who received an email attachment containing a PDF?
By running ‘grep -r “pdf” Desktop/phish-emails’, I was able to determine which eml file contained a pdf, and by opening that file I was able to find a name.

<img width="721" height="58" alt="question1" src="https://github.com/user-attachments/assets/188ee2f5-1006-4546-a370-03ad6cc29f10" />

### 2) What email address was used by the adversary to send the phishing emails? 
I simply opened the file and looked at who sent the emails. 

### 3) What is the redirection URL to the phishing page for the individual Zoe Duncan? (defanged format)
I downloaded and viewed the html code from Zoe Duncan’s email, found the redirection link, and using CyberChef, I defanged the link.

<img width="902" height="251" alt="question3" src="https://github.com/user-attachments/assets/a11f67ad-a12a-4515-858f-e070d66c7824" />

### 4) What is the URL to the .zip archive of the phishing kit? (defanged format)
I navigated to the link provided by the attachment, and by enumerating the website url, I eventually landed upon the page containing the .zip file.

<img width="594" height="241" alt="question4" src="https://github.com/user-attachments/assets/add7ebc2-2400-4f82-9b2a-e0ade9ed3608" />

### 5) What is the SHA256 hash of the phishing kit archive?
I downloaded the .zip file and ran “sha256sum Update365.zip to find the SHA256 hash of the phishing kit archive.

<img width="584" height="72" alt="question5" src="https://github.com/user-attachments/assets/9a97c971-7efb-43a4-9704-8ba00437b743" />

### 6) When was the phishing kit archive first submitted? (format: YYYY-MM-DD HH:MM:SS UTC)
Using VirusTotal and submitting the hash, I navigated to the details page and found the answer.

<img width="567" height="230" alt="question6" src="https://github.com/user-attachments/assets/2e218064-1a8d-48e4-9cb5-b45e0ad12fac" />

### 7) When was the SSL certificate the phishing domain used to host the phishing kit archive first logged? (format: YYYY-MM-DD)
I used crt[.]sh to view certificate transparency logs, scrolled down to the end to see when the phishing kit archive was first logged.

<img width="957" height="403" alt="question7" src="https://github.com/user-attachments/assets/bf8f1a62-29c2-409a-8f1b-aed3cac04db8" />

### 8) What was the email address of the user who submitted their password twice?
By enumerating the website I found log.txt which logged every credentials and I saw who sent their credentials twice.

### 9) What was the email address used by the adversary to collect compromised credentials?
After unzipping the Update365, I used grep to find a list of all emails written into the folder.

```grep -ErhoI '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' | sort -u```

### 10) The adversary used other email addresses in the obtained phishing kit. What is the email address that ends in "@gmail[.]com"?
I found the answer to this question using the same method above.

<img width="902" height="97" alt="question 910" src="https://github.com/user-attachments/assets/0ce2d716-19df-4177-9bfb-027f658e3a78" />

### 11) What is the hidden flag?
The hint indicated the flag was hidden in the phishing domain. After enumerating the domain, I found the hidden message. Realizing it was base64 encoded,
I decoded using CyberChef and reversed the output to obtain the final flag. 

<img width="811" height="465" alt="question11" src="https://github.com/user-attachments/assets/18c7ba4d-4bcc-4281-8b7a-d7241b1dedc8" />

