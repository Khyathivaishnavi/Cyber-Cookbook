# Cyber-Cookbook
**fuff tool**
A high-speed web fuzzer developed in Go.FFUF is one of the newest and fastest open-source fuzzing tools available. But before we dive in, let's understand what fuzzing is.

Fuzzing is the process of automatically providing random input to an application to find errors or unexpected behavior. It can also involve discovering hidden directories and files on a web server.

#How to install fuff in kali linux:
**Commmand: sudo apt-get install fuff**
![fuff install](https://github.com/Khyathivaishnavi/Cyber-Cookbook/assets/99657976/e98894a6-08fc-453a-8bd1-7a9275a531b8)

**Usage**
With the command **ffuf -h**. We can find the help page we can explore the tool with this command
![image](https://github.com/Khyathivaishnavi/Cyber-Cookbook/assets/99657976/98a6e8d1-ce95-420f-b60a-0ff7ba51d32f)

ffuf offers many options for fuzzing.

To specify the position to be fuzzed, use the word "FUZZ" in the ffuf command.

**Directory and File Discovery**
You can find directories on a website with the following command. It uses the -w flag to provide a wordlist and the -u flag to specify the URL with "FUZZ" as the placeholder for fuzzing.
**ffuf -w wordlist.txt -u http://website.com/FUZZ**
For file discovery, you can use the same command. To include specific file extensions from the wordlist, use the -e flag.
**ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html,.php,.txt**
![image](https://github.com/Khyathivaishnavi/Cyber-Cookbook/assets/99657976/dd9626ce-0f9f-4e7b-b3ab-e0b94837f378)

ffuf offers options to filter responses by specific status codes, line counts, response sizes, word counts, and regex patterns.

**Filtering Options**
**-mc**: Status code
**-ml**: Number of lines in the response
**-mr**: Regex pattern
**-ms**: Response size
**-mw**: Number of words in the response
**Examples**
To get responses with status codes 200 and 302, use:
**Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html -mc 200,302**
**Recursion**
URL parameters ending with FUZZ support recursion. The -recursion flag activates this, allowing ffuf to fuzz URLs and then fuzz further within the directories it discovers.
**-recursion-depth**: Specifies the depth of recursion
**-maxtime**: Sets a maximum time in seconds for the fuzzing process
**-maxtime-job**: Used with -recursion to set a maximum time for each new job created per directory found

Example for a maximum fuzzing time of 60 seconds:
**Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -maxtime 60**
