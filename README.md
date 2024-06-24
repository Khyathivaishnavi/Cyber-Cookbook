# Cyber-Cookbook
**fuff tool**
A high-speed web fuzzer developed in Go.FFUF is one of the newest and fastest open-source fuzzing tools available. But before we dive in, let's understand what fuzzing is.
<br/>
Fuzzing is the process of automatically providing random input to an application to find errors or unexpected behavior. It can also involve discovering hidden directories and files on a web server.
<<br/>
#How to install fuff in kali linux:<br/>
**Commmand: sudo apt-get install fuff**<br/>
![fuff install](https://github.com/Khyathivaishnavi/Cyber-Cookbook/assets/99657976/e98894a6-08fc-453a-8bd1-7a9275a531b8)
<br/>
**Usage**<br/>
With the command **ffuf -h**. We can find the help page we can explore the tool with this command<br/>
![image](https://github.com/Khyathivaishnavi/Cyber-Cookbook/assets/99657976/98a6e8d1-ce95-420f-b60a-0ff7ba51d32f)
<br/>
ffuf offers many options for fuzzing.<br/>
<br/>
To specify the position to be fuzzed, use the word "FUZZ" in the ffuf command.<br/>
<br/>
**Directory and File Discovery**<br/>
You can find directories on a website with the following command. It uses the -w flag to provide a wordlist and the -u flag to specify the URL with "FUZZ" as the placeholder for fuzzing.<br/>
**ffuf -w wordlist.txt -u http://website.com/FUZZ**<br/>
For file discovery, you can use the same command. To include specific file extensions from the wordlist, use the -e flag.<br/>
**ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html,.php,.txt**<br/>
![image](https://github.com/Khyathivaishnavi/Cyber-Cookbook/assets/99657976/dd9626ce-0f9f-4e7b-b3ab-e0b94837f378)
<br/>
ffuf offers options to filter responses by specific status codes, line counts, response sizes, word counts, and regex patterns.<br/>
<br/>
**Filtering Options**<br/>
**-mc**: Status code <br/>
**-ml**: Number of lines in the response<br/>
**-mr**: Regex pattern<br/>
**-ms**: Response size<br/>
**-mw**: Number of words in the response<br/>
**Examples**<br/>
To get responses with status codes 200 and 302, use:<br/>
**Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html -mc 200,302**<br/>
**Recursion**<br/>
URL parameters ending with FUZZ support recursion. The -recursion flag activates this, allowing ffuf to fuzz URLs and then fuzz further within the directories it discovers.<br/>
**-recursion-depth**: Specifies the depth of recursion<br/>
**-maxtime**: Sets a maximum time in seconds for the fuzzing process<br/>
**-maxtime-job**: Used with -recursion to set a maximum time for each new job created per directory found<br/>
<br/>
Example for a maximum fuzzing time of 60 seconds:<br/>
**Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -maxtime 60**<br/>
