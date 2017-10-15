Setup JAVA development environment on Visual Studio Code.

Windows
=======

Install chocolatey
------------------

In administrative shell, and run this command.

~~~sh
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
~~~

See also
- [How to: Install chocolatey](https://chocolatey.org/install)
- [How to: Start a Command Prompt as an Administrator](https://technet.microsoft.com/en-us/library/cc947813%28v=ws.10%29.aspx?f=255&MSPPError=-2147217396)


Install visual studio code
--------------------------

In administrative shell, run

~~~sh
choco install -y visualstudiocode
~~~

Install visual studio code extensions
-------------------------------------

In administrative shell, run

~~~sh
code install-extention streetsidesoftware.code-spell-checker
code install-extention robertohuertasm.vscode-icons
code install-extention vscjava.vscode-java-pack
~~~


Install maven and JDK
---------------------

In administrative shell, run

~~~sh
choco install -y maven
~~~

This will also install latest JDK into your system.

Make sure JAVA_HOME is set to JDK.

~~~sh
setx JAVA_HOME "C:\Program Files\Java\jdk1.8.0_144" /M
~~~


Create a new java project
-------------------------

Suppose you place all projects in **C:\code**, cd to this folder, and run this command:
~~~sh
mvn archetype:generate -DgroupId=com.kiloblue.app -DartifactId=hello_world -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
~~~
This will create a sub folder **hello_world**

Open this folder in VSCode by
~~~sh
code hello_world
~~~

In **Debug** Side Panel, configure launch.json, and start debug the application.

~~~json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "java",
            "name": "Debug (Launch)",
            "request": "launch",
            "mainClass": "com.kiloblue.app.App",
            "args": ""
        },
        {
            "type": "java",
            "name": "Debug (Attach)",
            "request": "attach",
            "hostName": "localhost",
            "port": 0
        }
    ]
}
~~~



Setup git repository
--------------------

Add **.gitignore** in your project's root folder, and add these lines:
~~~
log/
target/
~~~

Open integrated terminal by pressing **Ctrl+`**

Run these commands:
~~~sh
git init
git add --all
git commit -m "Initial commit"
git remote add origin https://github.com/lichr/java-vscode-hello.git
git push -u origin master
~~~