<h1>Applying Encryption and Hashing Algorithms for Secure Communications</h1>
<h2>Description</h2>
<p>Project consists of common cryptographic techniques to ensure confidentiality, integrity, and authentication. I will create MD5 checksum and SHA-1 hashes on simple text files on a Linux virtual
machine (VM) and compare the hash values of the original files with those generated after the file has been modified. Then, I will use GnuPG (Gnu Privacy Guard) to generate an encryption key pair and encrypt a message. Finally, I will utilize those key pairs to send secure messages between two user accounts on the virtual machine and verify the integrity of received files</p>
<br />
<h2>Utilities Used</h2>

- <b>gedit Text Editor</b>
- <b>Linux Machine</b>
- <b>GnuPG key generator tool</b>
<h2>Environments Used</h2>
- <b>Linux </b>

<h2>Lab Walk-through:</h2>
On my virtual desktop, I will open a remote connection to the TargetLinux01(student) machine by double clicking the <b>TargetLinux01 RDP shortcut</b> in the <b>Connections folder</b>. After I login into the machine, I open the gedit text editor. In the gedit window, I type "This is an example", then click the <b>Save</b> button on the gedit toolbar to open the Save As dialog box. In the Save As dialog box, I navigate to the Documents folder (<b>student</b> > <b>Documents</b>), then I type "Example.txt" in the Name box and click <b>Save</b> to save the .txt file. I go ahead and close the gedit window.
<h3>Create a MD5sum and SHA1sum Hash String</h3>
On the Linux machine, I open a terminal and execute <i>md5sum --help</i>, to get a little reivew of the process and options for this tool. On the command prompt, I execute <i>cd documents</i> to change the current directory to the Documents folder.
At the command prompt, I execute <i>ls -l</i>, to list the files in the Documents folder then I execute <i>cat Example.txt</i> to view the contents of the .txt file I created earlier.
Concatonate Example.txt file <br/>
<img src="https://i.imgur.com/BPp9Yg7.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
Still at the command prompt, I execute <i>md5sum Example.txt</i> to create an MD5sum hash string for the Example.txt file. This tool return a string of hexadecimal numbers that will be unique to my file on this virtual session.
<br/>
<img src="https://i.imgur.com/xaZZdKe.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
At the command prompt, I execute <i>md5sum Example.txt > Example.txt.md5</i> to store the MD5sum hash string for the Example.txt file in a new file. I continue and execute <i>ls</i> to list the files in the student folder and verify that the new Example.txt.md5 file has been added to the Documents folder.
At the command prompt, I execute <i>cat Example.txt.md5</i> to view the contents of the file. It is the same MD5sum hash string I created earlier, as shown below.
<br/>
<img src="https://i.imgur.com/fNXwx4X.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
Back at the command prompt, I execute <i>md5sum -c Example.txt.md5</i> to check the MD5sum hash created for the Example.txt file. If the file has not been modified, the system will display the words "Example.txt: OK (shown above), indicating that the hash is the same for both. Now, at the command prompt I execute <i>sha1sum Example.txt</i> to create a SHA1sum hash string for the Example.txt file. The tool will return a sting of hexadecimal numbers that will be unique to that file only.
<br/>
<img src="https://i.imgur.com/EttNMpk.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
Returning to the command prompt, I execute <i>sha1sum Example.txt > Example.txt.sha1</i> to store the SHA1sum hash string for the Example.txt file in a new sha1 file. I want to verify that the new Example.txt.sha1 file has been added to the Documents folder. I execute <i>ls</i> to list the files in the student folder. Next, I execute <i>cat Example.txt.sha1</i> to view the contents of the Example.txt.sha1 file and I see the same string hexadecimal characters created earlier.
<br/>
<img src="https://i.imgur.com/twwM8aT.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
Next, I execute <i>sha1sum Example.txt.sha1</i> to check the SHA1sum created for the Example.txt file. If the file has not been modified, the system will display "Example.txt: OK", indicating that the SHA1sum hash is the same for both.
<br/>
<h3>Modify a File and Verify Hash Values</h3>
At the command prompt, I execute <i>echo Jacob >> Example.txt</i> to add my name at the end of the Example.txt file, modifying its contents. Next, I execute <i>cat Example.txt</i> to view the contents of the modified .txt file. Back at the command prompt, I execute <i>md5sum Example.txt</i> to create an MD5sum hash string for that modified Example.txt file. The command will return a string of hexidecimal numbers that does not match the original string created from the orginal Example.txt file.
<br/>
<img src="https://i.imgur.com/x7wgYte.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
At the command prompt, I execute <i>sha1sum Example.txt</i> to create a SHA1sum hash string for the modified Example.txt file, returning a new hash string of hexidecimal numbers, different than the orginal string from the original Example.txt file.
<br/>
<img src="https://i.imgur.com/54bFjie.png" height="80%" width="80%" alt="Linux command line steps"/>
<h3>Generate GnuPG Keys</h3>
I'm still logged in as the student user. At the command prompt, I execute <i>gpgp --gen-key</i> to initiate the process for generating a public encryption key. When I'm prompted by the key generator I type the following answers for each response to the onscreen questions, pressing <b>Enter</b> after each entry:

- I choose <b>1</b> for my key type selection
- I enter <b>1024</b> for a key size of 1024 bits
- When asked "Key is valid for?", I enter <b>0</b> so that the key does not expire  at all.
- To confirm my choices, I enter <b>y</b> (for yes) saying it's correct.
<br/>
<img src="https://i.imgur.com/caiUdOY.png" height="60%" width="60%" alt="Linux command line steps"/>
<br />
Further into the key generator, I type the following answers in response to the request for a user ID to identify my key, pressing <b>Enter</b> after each entry.

- Real name: <b>Student</b>
- Email address: <b></b>
- Comment: <b></b>
- Change (N)ame, (C)omment, (E)mail or (O)kay//(Q)uit?: <b></b>
- Passphrase: <b></b>
- Repeat Passphrase: <b></b>

Then the system should display an error message: <i>Not enough random bytes available.</i> So, I open a second terminal window and resize both windows to fit on the desktop. At the command prompt, I execute <i>./entropy_loop.sh</i> to run a script that will "keep the machine busy" while generating a key pair.
<br/>
<img src="https://i.imgur.com/5hbe79p.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
While that script is running in the background, I click the first terminal window to activate it. Within three to five minutes there should be a reappearance of the command prompt, indicating that sufficient bytes were available to create the GPG key. After confirming the command prompt returns to the first terminal window, I close the second terminal window. Back at the command prompt (on the 1st terminal window) I execute <i>gpg --export -a > student.pub</i> to save the GnuPG key to a new file called student.pub. At the command prompt, I execute <i>pwd</i> to determine which working directory (wd) I'm currently using. It should display /home/student/Documents, indicating that I'm in the user, student's, Documents folder.
<br/>
<img src="https://i.imgur.com/L2P4D6Y.png" height="60%" width="60%" alt="Linux command line steps"/>
<br />
Next, I execute <i>ls</i> to list the files in the Documents folder and verify that the student.pub file was saved to the correct user account and location.
<br/>
<img src="https://i.imgur.com/YgoU7US.png" height="60%" width="60%" alt="Linux command line steps"/>
<br />
Now, I want to generate a GnuPG key for the Instructor account. Back at the command prompt, I execute <i>su Instructor</i> to switch to the Instructor account. When I'm prompted for the password, I enter "instructor". At the command prompt, I execute <i>cd /home/Instructor</i> to change directories to the Instructor folder.
<br/>
<img src="https://i.imgur.com/G196clf.png" height="60%" width="60%" alt="Linux command line steps"/>
<br />
I'm essentially performing the same process for generating a key for the Student account and proceed to create the GnuPG keys for the Instructor account with the following identification:

- Real name: <b></b>
- Email address: <b></b>
<br/>
<img src="https://i.imgur.com/0ulhPZj.png" height="80%" width="80%" alt="Linux command line steps"/>
<br />
Once the command prompt returns in the first terminal window, I execute <i>gpg --export -a > instructor.pub</i> to save the GnuPG key to a new file called instructor.pub. At the command prompt, I execute ls to list the files in the folder and verify that the instructor.pub file was saved correctly.
<br/>
<img src="https://i.imgur.com/ZH4CEBq.png" height="60%" width="60%" alt="Linux command line steps"/>
<br />
Returning to the command prompt, I type <i>exit</i> and <b>press Enter</b> to return to using the Student account.
<h3>Share GnuPG Key</h3>
Now I will share the public GnuPG key I just created for the Instructor account with the student account. This ensures that a file or message encrypted by a sender (student) can be decrypted by the recipient (Instructor). At the command prompt, I execute <i>cp /home/Instructor/instructor.pub /home/student/Documents/instructor.pub</i> to copy the instructor GnuPG keys (instructor.pub) to the student's Documents folder. At the command prompt, I execute <i>ls</i> to list the contents of the student folder and verify that the instructor.pub file is now included.
<br/>
<img src="https://i.imgur.com/Ihwuk0n.png" height="75%" width="75%" alt="Linux command line steps"/>
<br />
At the command prompt, I execute <i>gpg --list-keys</i> to list the current public key ring for the student account. For now, the key ring will show only the student.pub key. Soon, I will import the instructor's public key.
<br/>
<img src="https://i.imgur.com/0pMs6K4.png" height="75%" width="75%" alt="Linux command line steps"/>
<br />
At the command prompt. I execute <i>gpg --import instructor.pub</i> to import the instructor's GnuPG keys to the student public key ring. Again, I execute <i>gpg --list-keys</i> to list the updated public key ring for the student account as shown below.
<br/>
<img src="https://i.imgur.com/VwUEr05.png" height="75%" width="75%" alt="Linux command line steps"/>
<br />
<h3>Encrypt and Decrypt a ClearText Message</h3>
Now, I will use the GnuPG (Gnu Privacy Guard) to encrypt a cleartext message that I will send between the two fictitious users (Instructor and Student) I’ve mentioned throughout this demonstration. I will first generate a GnuPG key from the Student account, then generate a GnuPG key for the Instructor account.
At the command prompt, I execute <i>echo "this is a clear-text message from Jacob" > cleartext.txt</i> to save a clear-text message to a new file named <b>cleartext.txt</b>. Next, I exceute <i>gpg -e cleartext.txt</i> to encrypt the file. When the encryption process starts, I type the following responses, <b>pressing Enter</b> after each entry.

- Enter the [recipient] user ID. End with an empty line: <b>Instructor</b>
- Use this key anyway? (y/N): <b>y</b>
- Enter the user ID. End with an empty line: <b>press Enter</b>

Back at the command prompt, I execute <i>ls</i> to list the contents of the folder and verify that the encrypted file (cleartext.txt.gpg) has been created. At the command prompt, I execute <i>cat cleartext.txt.gpg</i> to view the contents of the encrypted file, as shown below.
<br/>
<img src="https://i.imgur.com/nYoq8bd.png)" height="75%" width="75%" alt="Linux command line steps"/>
<br />
