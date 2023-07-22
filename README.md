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
On the Linux machine, I open a terminal and execute _md5sum --help_, to get a little reivew of the process and options for this tool. On the command prompt, I execute 'cd documents' to change the current directory to the Documents folder. 
