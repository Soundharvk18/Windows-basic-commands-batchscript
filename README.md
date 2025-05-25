# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file
Save each script in a file with a .bat extension.
Ensure you have the necessary permissions to perform the operations.
Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "My-folder" on the desktop.


## COMMAND AND OUTPUT
```
mkdir my-folder
```
![image](https://github.com/user-attachments/assets/86f81423-f224-4b8b-bfd8-42868a5b4813)


## COMMAND AND OUTPUT
```
rmdir my-folder
```

![Screenshot 2025-05-15 182452](https://github.com/user-attachments/assets/39d9ce31-e4b7-4696-88cc-24cae9b6342b)

## COMMAND AND OUTPUT
```
COPY CON Rose.txt
```
A clock in a office can never get stolen
Too many employees watch it all the time
^Z
1 file(s) copied
```
dir Rose.txt
```

![Screenshot 2025-05-15 182616](https://github.com/user-attachments/assets/d7d3ff2a-ebcf-4137-af0d-433ce61324bf)

## COMMAND AND OUTPUT
```
echo “hello world” > hello.txt
type hello.txt
```
![Screenshot 2025-05-15 182725](https://github.com/user-attachments/assets/0c9ac47c-1ad8-4a18-ae46-2636b80e23a0)


## COMMAND AND OUTPUT
```
copy hello.txt hello1.txt
```
![Screenshot 2025-05-15 182831](https://github.com/user-attachments/assets/2fb8991f-cc54-40a3-a6d0-773f7646f1ab)



## COMMAND AND OUTPUT
```
del hello1.txt
dir hello1.txt
```
![Screenshot 2025-05-15 182917](https://github.com/user-attachments/assets/55c01d72-a4d7-4795-ae70-cc9f7af6a317)

## COMMAND AND OUTPUT
```
assoc | more
```
![Screenshot 2025-05-15 182956](https://github.com/user-attachments/assets/2f12209c-d688-448e-bfb6-fb56bc427007)

## COMMAND AND OUTPUT
```
fc hello.txt Rose.txt
```
![Screenshot 2025-05-15 183038](https://github.com/user-attachments/assets/75b011aa-a2e7-4095-a745-63fb11beb8e4)

## COMMAND AND OUTPUT

Open Notepad with filename 1.bat and type the following batch scrip
```
    @echo off
    set name=John
    echo Hello, %name%!
    pause
```
![Screenshot 2025-05-15 183258](https://github.com/user-attachments/assets/4de4c4d8-abc5-4a6f-ac26-1bddd2eda41f)

## COMMAND AND OUTPUT

Open Notepad with filename 2.bat and type the following and execute 2.bat
```
    @echo off
    :main
    set /p number=Enter a number: 
    rem Calculate remainder when divided by 2
    set /a remainder=%number% %% 2
    if %remainder%==1 (
        echo %number% is an odd number.
    ) else (
        echo %number% is not an odd number.
    )
    :choice
    set /p continue=Do you want to check another number? (Y/N): 
    if /i "%continue%"=="Y" goto main
    if /i "%continue%"=="N" goto end
    echo Invalid choice, please enter Y or N.
    goto choice
    :end
    echo Thank you for using the odd number checker!
    pause
```
![Screenshot 2025-05-15 183452](https://github.com/user-attachments/assets/640bb547-ff15-4e9b-ad36-433ed6b04cd9)

## Exercise 2: Advanced Batch Scripting
__1__.Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".

### BATCH PROGRAM

``` batch
@echo off
set name=John
echo Hello, %name%
pause
```



### OUTPUT


![hello_name](https://github.com/user-attachments/assets/8748d80d-52b1-4608-958f-f631c6f9ad1e)


__2__.Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

### BATCH PROGRAM
``` batch
@echo off
:loop
set /p num=Enter a number: 
set /a rem=%num% %% 2

if %rem%==0 (
    echo %num% is Even
) else (
    echo %num% is Odd
)

:ask
set /p ans=Do you want to check another number? (Y/N): 
if /I "%ans%"=="Y" goto loop
if /I "%ans%"=="N" goto end
echo Invalid input. Please enter Y or N.
goto ask

:end
echo Thank you!
pause
```

### OUTPUT
![check_odd](https://github.com/user-attachments/assets/b3c47388-b3d4-4d29-8238-cb4730e89d86)






__3__.Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.

### BATCH PROGRAM

``` batch
@echo off
for /L %%i in (1,1,5) do (
    echo Number: %%i
)
pause
```

### OUTPUT

![loopdisplay](https://github.com/user-attachments/assets/58cb1f3f-fffe-4738-a7b7-8a48a4ffb904)




__4__.Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

__Instructions:__
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

### BATCH PROGRAM

``` batch
@echo off
if exist sample.txt (
    echo sample.txt exists.
) else (
    echo sample.txt does not exist.
)
pause
```

### OUTPUT


![check_file](https://github.com/user-attachments/assets/7612b72a-5a67-461a-9910-ae55e072f49e)


__5__.Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.

### BATCH PROGRAM

``` batch
@echo off
:menu
cls
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
set /p choice=Choose an option (1-3): 

if "%choice%"=="1" goto hello
if "%choice%"=="2" goto create
if "%choice%"=="3" goto exit
echo Invalid choice.
pause
goto menu

:hello
echo Hello, World!
pause
goto menu

:create
echo This is a new file > newfile.txt
echo File newfile.txt created.
pause
goto menu

:exit
echo Goodbye!
pause
exit
```

### OUTPUT
![image](https://github.com/user-attachments/assets/2ded1d27-3cea-4812-a0f7-209e477c40fc)

![image](https://github.com/user-attachments/assets/44c2dcbf-c5e3-409a-9aff-0e30865b0ed5)

![image](https://github.com/user-attachments/assets/9706ff97-3d69-4f94-94a1-677f2f02f9b7)





# RESULT:
The commands/batch files are executed successfully.

