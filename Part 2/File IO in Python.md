#ACM Hack-It
## Python 3.x

### 1. Opening and Closing files

Till now we have been writing and reading data from the standard input and output. If we want to create our own files and store and retrieve data from them, then all we have to do is learn some more simple syntax. To begin with, how do we create and open a file?
For now, we will only be talking about working within one directory – that is, both the .py script and the file we are creating/writing to/deleting/renaming/etc will be in the same directory.
In python, we have the open() function. We specify two arguments: the file name and the access mode. Let us look at an example of where both the .py script, and the file we want to create, are both in the same directory.

``` file = open("myfile.txt","w+") ```

Since the file does not exist yet, it creates a new file called myfile.txt. The w+ argument tells Python that we want to be able to both read and write to the file. This is called the access mode. There are some different values we can supply here:
1. ```r``` For reading from a file only.  
2. ```r+``` For reading from and writing to a file.  
3. ```w``` For only writing to a file.
4. ```w+``` For reading to and writing from a file.
5. ```a``` For only appending to the end of a file.
6. ```a+``` For appending to and reading from the end of a file.  
When creating a file that does not exist, use either w, w+, a, or a+.  
We can close a file we have opened after working with it by using the ```close()``` function:  
``` file.close() ```

### 2. Writing to a file  
In order to write to a file, we have the ```write()``` function. It allows us to write any string into the file. For example, if I wanted to open a file called sid.txt and write the integers from 0 to 9 on separate lines in it, I could do this:  
``` python
1.	file=open("sid.txt","w+")  
2.	for i in range(10):  
3.	    file.write(str(i)+"\n")  
4.	file.close()  
```
The only new code here is the ```file.write()``` part. The ```write()``` function is a method of the file object that we created. It takes a string argument as input, and that’s what I supplied. The \n is simply telling to go to the next line after every number it writes into the file.
Of course, at the end, the ```file.close()``` closes the file to avoid any issues with data.

### 3. File Position  
If we want to know where we are in a current file, or read or write to a certain place, we need some sort of way to keep track of our position. We do this by talking in terms of bytes.  
When we create a new file we are at the beginning of the file – this is the zero byte location. As we read or write, this position changes. Fortunately, there are two functions that allow us to control position:
```
tell()    
seek(offset, from = 0)  
```
The ```tell()``` function is simple – it returns an integer value which tells you how many bytes from the beginning of the file you have moved. For example, if the only text in a file was this is a sentence, then if you read up to this I, and did file.tell(), it would return 7.  
The ```seek()``` function allows you to change where you are. The first argument it takes is how many bytes ahead you want to be located; the second optional argument specifies from where. For example:  
``` python
file=open("sid.txt","w+")  
file.seek(10)  
file.close()  
```
The above code places our current position at 10 bytes into the file. If we wanted to move 20 bytes ahead after the 5th byte, then we could write:  
``` python
file=open("sid.txt","w+")  
file.seek(20,5)  
file.close()  
```
### 4. Deleting and renaming a file
Since we just covered modules, we can quickly use them to show how to rename and delete a file. Suppose we have a file called trash.txt on the desktop. In order to rename it to good.txt, we can use the following bit of code:
``` python
import os
os.rename("trash.txt", "good.txt")
```
This of course assumes that we both the .py file and the file to be renamed are in the  same directory, as mentioned earlier.  
Similarly, the os module has a function that allows us to delete a file in the following way. Suppose the file called old.txt exists and we want to remove it:   
``` python
import os 
os.remove("old.txt")
```



