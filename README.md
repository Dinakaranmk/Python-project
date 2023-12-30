Check if two PDF documents are identical with Python
Python is an interpreted and general purpose programming language. It is a Object-Oriented and Procedural paradigms programming language. There are various types of modules imported in python such as difflib, hashlib.

Modules used:
difflib : It is a module that contains function that allows to compare set of data.
SequenceMatcher : It is used to compare pair of input sequences.
Function Used:
hash_file ( string $algo , string $filename , bool $binary = false ): It is a function which has the hash of a file.
object.hexdigest(): It is a function which returns string.
fileObject.read(size): It is a function that returns the specified number of bytes of a file.
Approach
Import module
Declare a function with 2 arguments which is for file.
Declare two objects for hashlib.sha1()
Open files
Read the file by breaking the line into smaller chunks
Now return both file such as h1.hexdigest() which is of 160 bits.
Use hash_file() function to store the hash of a file.
Compare and generate appropriate message
Program:


import hashlib 

from difflib import SequenceMatcher 

  

  

def hash_file(fileName1, fileName2): 

  

    # Use hashlib to store the hash of a file 

    h1 = hashlib.sha1() 

    h2 = hashlib.sha1() 

  

    with open(fileName1, "rb") as file: 

  

        # Use file.read() to read the size of file 

        # and read the file in small chunks 

        # because we cannot read the large files. 

        chunk = 0

        while chunk != b'': 

            chunk = file.read(1024) 

            h1.update(chunk) 

              

    with open(fileName2, "rb") as file: 

  

        # Use file.read() to read the size of file a 

        # and read the file in small chunks 

        # because we cannot read the large files. 

        chunk = 0

        while chunk != b'': 

            chunk = file.read(1024) 

            h2.update(chunk) 

  

        # hexdigest() is of 160 bits 

        return h1.hexdigest(), h2.hexdigest() 

  

  

msg1, msg2 = hash_file("pd1.pdf ", "pd1.pdf") 

  

if(msg1 != msg2): 

    print("These files are not identical") 

else: 

    print("These files are identical") 
