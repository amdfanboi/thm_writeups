# REvil Corp - TryHackMe

Room type : Challenge

Difficulty : Medium

Date completed : 18.10.2025 00:43 (10/18/2025 12:43 AM)

Link : https://tryhackme.com/room/revilcorp

## Scenario

One of the employees at Lockman Group gave an IT department the call; the user is frustrated and mentioned that all of his files are renamed to a weird file extension that he has never seen before. After looking at the user's workstation, the IT guy already knew what was going on and transferred the case to the Incident Response team for further investigation.

## Let's start

First, we start the VM and then connect to it using RDP and provided credentials.

![creds](https://github.com/user-attachments/assets/7f8d5ab6-3fc4-4e74-a2c1-d2c124e59a06)

You can also control the VM from the browser through the split view.

After connecting, we can start the investigation by opening the "AnalysisSession1" file located in the "Analysis File" folder on the Desktop.

It may take some time to load the file (approx. 2-3 minutes).

## Q1 : What is the compromised employee's full name?

To figure it out, we can simply just go to "System information" page.

After scrolling a little, you should notice the "User Information" section.

![userinfo](https://github.com/user-attachments/assets/c00c13e8-3096-466c-b6a0-99b8f109401e)

The answer here is the "Logged in User" which is John Coleman.

![q1_thm](https://github.com/user-attachments/assets/99cee199-1336-452a-a4d5-eef6eec8e155)

## Q2 : What is the operating system of the compromised host?

The answer can also be found on the "System Information" page.

Just look for "Operating System Information" section.

![osinfo](https://github.com/user-attachments/assets/d66a6019-40ac-4c2a-9492-f00ff34090ee)

The answer here is "Operating System" which is Windows 7 Home Premium 7601 Service Pack 1.

![q2_thm](https://github.com/user-attachments/assets/8db991ae-ff77-4486-bcf8-f2b4c1d3771e)

## Q3 : What is the name of the malicious executable that the user opened?

This time we need to go to "File System" page.

After scrolling a little bit, you should notice the file named WinRAR2021.exe located in C:\Users\John Coleman\Downloads.

(if you don't see it, then just uncheck all directories except Downloads)

![filesystem1](https://github.com/user-attachments/assets/5cd74e37-5375-49be-85cd-2c7135d8595e)

That means, the answer here is WinRAR2021.exe.

![q3_thm](https://github.com/user-attachments/assets/a1d52cb1-dec0-4e75-9985-d62034ba711a)

## Q4 : What is the full URL that the user visited to download the malicious binary? (include the binary as well)

Now we move to "File Download History" page.

There you should already notice the suspicious IP address which includes the filename provided earlier.

![filedl](https://github.com/user-attachments/assets/ddb945de-621f-42c2-a66a-605d14856e86)

The Source URL is the answer to this question.

![q4_thm](https://github.com/user-attachments/assets/3e9d763a-e698-41b8-8f73-d956f811dd3f)

## Q5 : What is the MD5 hash of the binary?

We need to go back to "File System" page.

After finding the binary, just scroll until you'll notice the MD5 hash.

![md5](https://github.com/user-attachments/assets/a4edd75b-ad89-49fa-9f9b-867681dfa389)

The MD5 hash you've found will be the answer here.

![q5_thm](https://github.com/user-attachments/assets/6a8bac14-75f4-4123-a5ab-a4545631582c)

## Q6 : What is the size of the binary in kilobytes?

Just scroll back until you'll notice the size of the binary.

![size](https://github.com/user-attachments/assets/932a01a2-b6d7-4314-a388-ce5943e77dd9)

The answer here is the number of kilobytes.

![q6_thm](https://github.com/user-attachments/assets/cf0ccafe-58a5-4d15-8c06-dd439f6e02c2)

## Q7 : What is the extension to which the user's files got renamed?

There are two ways to find out and both of them are very easy : 

- Look at the name of the ransom note (REvil's looks like [Random_Extension]-readme.txt)
- Look at the appended extension to some files

![filesystem2](https://github.com/user-attachments/assets/7ee70e9d-81da-44a3-a86f-6ce68e0bc89b)

At this point i think you already know the answer for this question.

![q7_thm](https://github.com/user-attachments/assets/af69b299-e24e-4522-90f5-9a28dfd6a8b5)

## Q8 : What is the number of files that got renamed and changed to that extension?

To find this out, we should now go to "Timeline" page.

Then uncheck everything except the "Modified" and "Changed" in the Files section.

![timeline](https://github.com/user-attachments/assets/00206ecc-aca3-41e6-b8c8-28f4112de703)

Then you should get the answer which is 48.

![q8_thm](https://github.com/user-attachments/assets/70060496-d624-4714-9db8-e659981b5a17)

(this question took me around 10 minutes as i didn't unchecked everything and i've eventually guessed the right answer)

## Q9 : What is the full path to the wallpaper that got changed by an attacker, including the image name?

Once again, we go back to "File System" page.

Then go to C:\Users\John Coleman\AppData\Local and check the Temp directory.

There should be a file named hk8.bmp which is a wallpaper.

![filesystem3](https://github.com/user-attachments/assets/67ba678e-8d18-44ac-a54a-ab7c567b0a8c)

So the answer here is the full location of the hk8.bmp file.

![q9_thm](https://github.com/user-attachments/assets/4fd80fe5-2a1c-4d58-beb1-b8b4ef1364d2)

## Q10 : The attacker left a note for the user on the Desktop; provide the name of the note with the extension.

If you remember what i've said while explaining the Q7, then i think you should already know what the answer for that question is.

![q10_thm](https://github.com/user-attachments/assets/a7035f48-3777-49de-b1bd-df4c60957770)

## Q11 : The attacker created a folder "Links for United States" under C:\Users\John Coleman\Favorites\ and left a file there. Provide the name of the file.

We stay in "File System" page and navigate to C:\Users\John Coleman\Favorites\Links for United States.

There you should notice an encrypted file named "GobiernoUSA.gov.url.t48s39la".

![filesystem4](https://github.com/user-attachments/assets/a37ea0e4-bcbe-4939-8a82-ad57873aeb9f)

This is the answer for that question.

![q11_thm](https://github.com/user-attachments/assets/7cb48401-d18f-430e-a625-c7df7d9e492b)

## Q12 : There is a hidden file that was created on the user's Desktop that has 0 bytes. Provide the name of the hidden file.

Now let's go back to C:\Users\John Coleman\Desktop.

If you'll scroll a little, you'll notice that there is a 0KB file name "d60dff40.lock"

![filesystem5](https://github.com/user-attachments/assets/a9febb2e-18c3-4cdc-af28-aecdde06472d)

So that means the answer here is d60dff40.lock

![q12_thm](https://github.com/user-attachments/assets/e9b96eb2-b4fe-410c-8090-f1e109145e2c)

## Q13 : The user downloaded a decryptor hoping to decrypt all the files, but he failed. Provide the MD5 hash of the decryptor file.

If you're still on the Desktop, then you've probably also noticed the file named d.e.c.r.yp.tor.exe.

In this case, just scroll until you'll notice the MD5 hash of the file.

![filesystem6](https://github.com/user-attachments/assets/463a2636-b5b9-4226-9c51-a031b3edc5c1)

This MD5 hash is the answer.

![q13_thm](https://github.com/user-attachments/assets/8e48bd6e-f276-4228-b963-619f0cba5f14)

## Q14 : In the ransomware note, the attacker provided a URL that is accessible through the normal browser in order to decrypt one of the encrypted files for free. The user attempted to visit it. Provide the full URL path.

The easiest way would be to acquire the ransom note and extract the URL... but we can't do that here.


So instead, we can just go to "Browser URL history" page and search for said URL.

After little scrolling, you should notice that the user visited "http://decryptor.top" a few times.

![favicon](https://github.com/user-attachments/assets/d1b8059e-32b5-4fcc-963e-c606b6e9ea04)

A quick search should give us the URL we need.

![decryptortop](https://github.com/user-attachments/assets/b04b2faa-1d53-4fe8-8820-e907de3f307e)

This URL is our answer.

![q14_thm](https://github.com/user-attachments/assets/98e08004-6432-476f-86b2-b8ed2b5ac5f4)

## Q15 : What are some three names associated with the malware which infected this host? (enter the names in alphabetical order)

We already know that one of the names is "REvil". So how can we find the other ones?

We can always get the MD5 of the ransomware's binary and search it on VirusTotal.

![detectionpage](https://github.com/user-attachments/assets/ff40675c-7956-430c-aacf-e058524f4dff)

You can already notice in the family labels that the other names are "Sodin" and "Sodinokibi".

So the answer would be REvil, Sodin, Sodinokibi

![q15_thm](https://github.com/user-attachments/assets/5cbf159d-1126-4a32-bd98-d6b7f5d365a2)

## The end.

Thank you for reading my first write-up.

I hope it helped.


~ Yurippe ❤️
