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

<h2>Program Walk-through:</h2>
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
