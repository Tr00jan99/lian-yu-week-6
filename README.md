# 🏝️ Lian Yu


### 📘 LAB WEEK 6

### 
### 👤 MUHAMMAD SYAFIQ BIN RIDZUAN

### 
### 🆔 52215125897

### 
### 📖 IKB21403
### -
### 🔐 VULNERABILITY ANALYSIS

---

1. Accessing the TryHackMe room "Lian_Yu" and viewing the target machine
information and task list.
><img width="940" height="500" alt="image" src="https://github.com/user-attachments/assets/bf41c83d-9708-4c06-a51e-43db2d2f6f71" />

2. Initializing the target machine with IP address 10.48.145.10
><img width="940" height="524" alt="image" src="https://github.com/user-attachments/assets/2d6370a5-b770-4522-884a-da783d72c77b" />

---

3. Running an Nmap scan (nmap -sC -sv) which revealed open ports 21 (FTP), 22
(SSH), 80 (HTTP), and 111 (RPC
><img width="940" height="556" alt="image" src="https://github.com/user-attachments/assets/18da8478-3b4f-4039-a9ec-3c57ed0c6065" />

4. Navigating to the web server's homepage titled "Purgatory" featuring an
Arrowverse theme
><img width="940" height="463" alt="image" src="https://github.com/user-attachments/assets/0854dafd-25e3-4ab5-bd38-e64fb8297c0b" />

---

5. Executing gobuster for directory enumeration and discovering the /island directory.
><img width="940" height="464" alt="image" src="https://github.com/user-attachments/assets/2cc3d1ec-bb25-4a95-9270-364a28371d3a" />

6. Accessing the /island directory on the web browser.
><img width="940" height="429" alt="image" src="https://github.com/user-attachments/assets/97356d1c-eb45-4772-a0c2-ccad8d599cfe" />


---

7. Inspecting the page source of /island and finding a hidden "Code Word" which is
vigilante
><img width="940" height="432" alt="image" src="https://github.com/user-attachments/assets/1136649b-5476-44ff-98ba-e46306b99a3a" />

8. Running another gobuster scan on the /island directory and finding the /2100
subdirectory.
><img width="940" height="601" alt="image" src="https://github.com/user-attachments/assets/9eee101e-2c92-46ca-86dc-5510a30f60bf" />


---

9. Accessing the hidden /island/2100/ directory in the browser
><img width="940" height="423" alt="image" src="https://github.com/user-attachments/assets/2279cd5f-7fd4-4ab3-8c2b-49c9e80c7bd4" />

10. Viewing the page source of /2100 and finding a comment hint: "you can avail
your .ticket here but how?"
><img width="940" height="454" alt="image" src="https://github.com/user-attachments/assets/1a270e56-93bf-415a-a03c-292b3a49fdf0" />


---

11. Using gobuster with the -x .ticket extension to find the file green_arrow.ticket.
><img width="940" height="520" alt="image" src="https://github.com/user-attachments/assets/57f397b0-1628-4d59-979b-b15ebda49c0a" />

12. Opening green_arrow.ticket to reveal a Base58 encoded token: RTy8yhBQdscX
><img width="940" height="422" alt="image" src="https://github.com/user-attachments/assets/54c32dc2-6969-48e9-b706-9a66ca53a928" />


---

13. Using CyberChef to decode the Base58 string, resulting in the plaintext
password !#th3h00d.
><img width="525" height="244" alt="image" src="https://github.com/user-attachments/assets/b4a3aeff-4560-4ced-8c4b-1723f018cd7a" />


---

14. Successfully logging into the FTP server using the credentials
vigilante:!#th3h00d
><img width="940" height="475" alt="image" src="https://github.com/user-attachments/assets/b0bdff56-a798-4179-96c6-a61964f5a3e0" />

15. Listing and downloading files from the FTP server: Leave_me_alone.png,
Queen's_Gambit.png, and aa.jpg
><img width="940" height="658" alt="image" src="https://github.com/user-attachments/assets/3ce81b07-2525-448f-a217-0ca6ec7ee7c9" />

---

16. Attempting to open Leave_me_alone.png and encountering a "Not a PNG file"
error.
><img width="863" height="563" alt="image" src="https://github.com/user-attachments/assets/55e8d229-5820-4370-91da-64f13d1de43b" />

17. Running exiftool on the image, confirming a file format error.
><img width="781" height="241" alt="image" src="https://github.com/user-attachments/assets/b22594a0-8fe1-4965-9be8-00b4d2277e6b" />


---

18. Using xxd to inspect the hex header, showing incorrect magic numbers.
><img width="850" height="264" alt="image" src="https://github.com/user-attachments/assets/f5fb5bde-4979-41a8-acbc-cb98454f0ef8" />

19. Using hexdump to further analyze the corrupted file header
><img width="940" height="425" alt="image" src="https://github.com/user-attachments/assets/10cc786f-72e3-4a30-8e0f-fa520a31f3a1" />


---

20. Referencing standard PNG file signatures to identify the correct magic numbers.
><img width="940" height="308" alt="image" src="https://github.com/user-attachments/assets/89d2c6ec-1af1-4dfe-91ac-80cce1977df3" />

21. Executing a Python one-liner to overwrite the corrupted header with the correct
PNG magic numbers
><img width="940" height="695" alt="image" src="https://github.com/user-attachments/assets/165800f9-d66c-43ad-b8c8-ef05004f40e0" />

---

22. Successfully opening the repaired Leave_me_alone.png which displays a
"password" hint.
><img width="940" height="474" alt="image" src="https://github.com/user-attachments/assets/28761544-1b4c-42b5-a035-d2e04ecf666f" />

23. Using steghide to extract hidden data from aa.jpg, resulting in a file named ss.zip
><img width="864" height="440" alt="image" src="https://github.com/user-attachments/assets/83c59baf-2f9c-4b5d-ac09-94a743e883c4" />


---

24. Unzipping ss.zip to find two files: passwd.txt and shado
><img width="825" height="383" alt="image" src="https://github.com/user-attachments/assets/ad632da6-f0f0-43b0-a41d-f59a4d4b2373" />

25. Reading the contents of the shado file to find the password M3tahuman.
><img width="894" height="663" alt="image" src="https://github.com/user-attachments/assets/9717dded-1c3d-4962-bdfb-b0980c4678d7" />


---

26. Successfully logging in via SSH as the user slade using the discovered
password.
><img width="485" height="208" alt="image" src="https://github.com/user-attachments/assets/740a82e8-0d04-48db-b2ba-348b3301fe8c" />

27. Locating and reading user.txt to capture the first flag.
><img width="916" height="196" alt="image" src="https://github.com/user-attachments/assets/c8e52174-2205-46ba-9ad4-c094fef84256" />


---

28. Running sudo -l and discovering that slade can run /usr/bin/pkexec as root.
><img width="916" height="196" alt="image" src="https://github.com/user-attachments/assets/2a00e80d-3d6b-456c-9394-186f712a3308" />

29. Exploiting pkexec to gain root access and reading the final root.txt flag.
><img width="940" height="431" alt="image" src="https://github.com/user-attachments/assets/f5894775-1077-4c29-b344-dddd281a912b" />

30. Final confirmation screen showing the room "Lian Yu" has been 100%
completed.
><img width="818" height="575" alt="image" src="https://github.com/user-attachments/assets/6480ad6a-b627-42a2-bfde-3199ccdc92e7" />


---



---
