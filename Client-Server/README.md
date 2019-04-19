# ECE568 HW6  

By *Yilun Miao(ym339)*

#### Install Running Environment

- Install 1.8 java version with jdk1.8.0_144 and jre1.8.0_144
- Install latest <u>Intellij IDEA</u> as an option

#### Compile and Run programs

###### Using IDE to compile and run files

- Open <u>Client.java</u> as a project in IDE
- Edit Configurations in IDE and set *Program Arguments* with <host name> and <port number>
- Open <u>Server.java</u> as a project in IDE
- Edit Configurations in IDE and set *Program Arguments* with <port number>
- Compile and run both projects in IDE

###### Using terminal to compile and run files

- Open terminal and enter the directory of files <u>Client.java</u> and <u>Server.java</u>
- Enter ***javac Client.java*** to compile <u>Client.java</u>
- Enter ***javac Server.java*** to compile <u>Server.java</u>
- Open Another terminal
- Enter ***java Server <port number>*** to run the server in one terminal
- Enter ***java Client <host name>  <port number>*** to run a client in another terminal
- The arguments of <port number> should remain the same for server and client
- If you run both client and server in your local environment, you should enter ***localhost*** as host name

#### Commands Supported

```html
GET <filename>
```

You could use ***GET*** to achieve files from server if the file exists. If the server does not have such a file, the server would response with a error message.



```html
BOUNCE <text-to-bounce>
```

You could bounce some specific text to the server. If the server successfully receive the bounced text, it would send back a success message.



```html
EXIT <exit-code>
```

You could use exit the server with some exit code. The exit code is optional, you could choose to exit with some exit code or without exit code.



#### Testcase

###### Invalid Command

```markdown
Enter the Command: POST
    Unknown command.

    GET <filename>:
         Return the content of filename from the server.
    BOUNCE <msg>:
          Send a message to the server.
    EXIT [code]:
          Disconnect from server, and send a code to server (optinal).

```

###### Get non-exist file

```markdown
Enter the Command: GET word.txt
    Command received by server.
    ERROR: no such file

```

###### Get exited file

```markdown
Enter the Command: GET test.txt
    Command received by server.

======File content starts======
This is a test file.
Hello
World
!
======File content ends======

```

###### Bounce some text

```markdown
Enter the Command: BOUNCE hello world!
    Command received by server.

Bounce Message Success
hello world!
```

###### Bounce without text

```
Enter the Command: BOUNCE
    Missing parameters.
    GET <filename>:
         Return the content of filename from the server.
    BOUNCE <msg>:
          Send a message to the server.
    EXIT [code]:
          Disconnect from server, and send a code to server (optinal).
          
```

###### Exit without code

Client Side:

```markdown
Enter the Command:  EXIT
    Command received by server.
    Exit Server! Bye!
    Disconnected from server successfully.

```

Server Side:

```markdown
Waiting for commands from client...
    A client connects to server.
    Normal exit
  A client disconnects from server.
```



###### Exit with exit code

Client Side:

```markdown
Enter the Command: EXIT CHROME_ERRORCODE_123.4.5
    Command received by server.
    Exit Server! Bye!
    Disconnected from server successfully.

```

Server Side:

```markdown
Waiting for commands from client...
    A client connects to server.
    Message from client: CHROME_ERRORCODE_123.4.5
  A client disconnects from server.
```

