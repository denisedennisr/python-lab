<h1>Update a file through Python Algorithm</h1>

<h2>Description</h2>
In my workplace, we manage restricted content access using an IP address whitelist. The whitelist is maintained through a file called "allow_list.txt," which contains the approved IP addresses. Additionally, there is a separate list for IP addresses that should no longer have access, referred to as the removal list. I developed an algorithm to streamline the process of updating the "allow_list.txt" file by automatically removing the IP addresses that should no longer have access to the content.
<br />
<h2>Program walk-through:</h2>

<h2>Open the file that contains the allow list</h2>
In the initial step of the algorithm, I initiated the process by accessing the "allow_list.txt" file. To begin with, I stored the filename as a string within the import_file variable:
<br />
<img src="https://imgur.com/bx3AH0s.png" height="80%" width="80%" alt="Python Steps"/>
<br />
<br />
The 'with' statement is then used to open the file 
<br/>
<img src="https://imgur.com/qIvTIQA.png" height="80%" width="80%" alt=" Python Steps"/>
<br />
<br />
Within my algorithm, I utilize the "with" statement in conjunction with the ".open()" function set to read mode to access the allow list file for reading purposes. The primary objective of opening the file is to gain access to the IP addresses stored within it. By employing the "with" keyword, I ensure proper resource management by automatically closing the file upon exiting the "with" statement.
In the code snippet "with open(import_file, 'r') as file:", the "open()" function takes two parameters. The first parameter specifies the file to be imported, while the second parameter defines the intended file operation. In this instance, "r" signifies that I intend to read the file. The code also employs the "as" keyword to assign the variable named "file," which holds the output of the ".open()" function while I work within the "with" statement.
<br>
<br>
<h2> Read the file contents</h2>
In order to read the file contents, I used the .read() method to convert it into the string.
<img src="https://imgur.com/mvgBicH.png" height="80%" width="80%" alt=" Python Steps"/>
<br />
<br />
When utilizing the ".open()" function with the "r" argument denoting "read," I have the capability to invoke the ".read()" method within the "with" statement's body. The ".read()" method serves the purpose of converting the file's contents into a string, enabling me to peruse its contents. I applied the ".read()" method to the "file" variable identified within the "with" statement, subsequently storing the resulting string in a variable named "ip_addresses."
In summary, this piece of code reads the content of the "allow_list.txt" file and transforms it into a string format. This string can then be utilized in my Python program for the organization and extraction of data.
<h2> Convert the string into a list </h2>
In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the .split() method to convert the ip_addresses string into a list:
<br>
<br>
<img src="https://imgur.com/Bsa2MWS.png" height="80%" width="80%" alt="Python Steps"/>
<br />
<br />
The ".split()" function is invoked by attaching it to a string variable. Its function is to transform the contents of a string into a list structure. The intention behind splitting the "ip_addresses" string into a list is to facilitate the removal of IP addresses from the allow list. By default, the ".split()" function breaks down the text into list elements based on whitespace. In this algorithm, the ".split()" function operates on the data stored in the "ip_addresses" variable, which contains a string of IP addresses separated by whitespace. It then transforms this string into a list of IP addresses. To store this resultant list, I reassigned it back to the "ip_addresses" variable.  <br/>
<br />
<br />
<h2> Iterate through the remove list</h2>
An essential component of my algorithm entails cycling through the IP addresses contained within the "remove_list." To accomplish this, I integrated a for loop:
<br>
<br>
<img src="https://imgur.com/5wyAzHW.png" height="80%" width="80%" alt="Python Steps"/>
<br />
<br />
In Python, a for loop is used to execute code repeatedly for a defined sequence. In algorithms written in Python, such as this one, the primary objective of a for loop is to apply specific code instructions to every element within a given sequence. The for loop begins with the "for" keyword, followed by the loop variable (in this context, "element"), and the "in" keyword. The "in" keyword signifies the iteration through the "ip_addresses" sequence, assigning each value to the loop variable "element." <br/>

<h2>Remove IP addresses that are on the remove list</h2>
In my algorithm, the task involves removing any IP address from the "ip_addresses" allow list if it is also found in the "remove_list." Since there were no duplicates in "ip_addresses," I  was able to employ the following code to achieve this:

<img src="https://imgur.com/v5Cz16W.png" height="80%" width="80%" alt="Python Steps"/>
First, within my for loop, I established a condition to assess whether the loop variable "element" existed in the "ip_addresses" list. This check was essential because attempting to use the ".remove()" method on elements not present in "ip_addresses" could lead to an error.
Subsequently, within that conditional block, I employed the ".remove()" method on "ip_addresses." I provided the loop variable "element" as an argument to ensure that each IP address contained in the "remove_list" would be successfully removed from the "ip_addresses" list.
<br> 
<br>
<h2>Update the file with the revised list of IP addresses </h2>
<br>
<br>
As a final step in my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do so, I first needed to convert the list back into a string. I used the .join() method for this:
<img src="https://imgur.com/NNtiPtv.png" height="80%" width="80%" alt="Python Steps"/>
<br>
<br>

The ".join()" method merges all the elements in an iterable into a single string. This method is employed by attaching it to a string that defines the characters to be used as separators between the elements in the iterable once they are combined into a string. In this particular algorithm, I utilized the ".join()" method to construct a string from the "ip_addresses" list. This string was intended to be passed as an argument to the ".write()" method when writing to the "allow_list.txt" file. I chose the string ("\n") as the separator to instruct Python to place each element on a new line.Then, I used another with statement and the .write() method to update the file:
<img src=https://imgur.com/LKcFltE.png" height="80%" width="80%" alt="Python Steps"/>
<br>
<br>
This time, I incorporated a second argument, "w," when using the "open()" function within my "with" statement. This argument signifies my intention to open a file for writing and overwrite its existing contents. By using "w" as the argument, I gained the capability to employ the ".write()" function within the "with" statement's body. The ".write()" function is employed for writing string data to a designated file and overwriting any preexisting content.
In this scenario, my objective was to write the updated allow list as a string to the "allow_list.txt" file. This approach ensures that restricted content will no longer be accessible to any IP addresses removed from the allow list. To perform this file rewriting operation, I appended the ".write()" function to the "file" object, which was initially defined within the "with" statement. As an argument, I passed in the "ip_addresses" variable to specify that the contents of the file identified in the "with" statement should be replaced with the data contained in this variable.
<br>
<br>
<h2>Summary</h2>

I designed an algorithm for the purpose of eliminating IP addresses specified in a "remove_list" variable from the "allow_list.txt" file, which contains a list of authorized IP addresses. This algorithm entailed several steps, starting with the opening of the file, converting its content into a readable string, and subsequently transforming this string into a list, which was stored in the "ip_addresses" variable.
Next, I iterated through the IP addresses contained in the "remove_list." During each iteration, I checked whether the element existed within the "ip_addresses" list. If it did, I applied the ".remove()" method to eliminate the element from the "ip_addresses" list.
Following this, I employed the ".join()" method to convert the "ip_addresses" list back into a string. This string was then utilized to overwrite the contents of the "allow_list.txt" file with the updated list of IP addresses.

