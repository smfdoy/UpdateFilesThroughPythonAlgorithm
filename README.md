<h1>Update files through Python Algorithm</h1>

 ### 

<h2>Project Description</h2>
At my organization, access to restricted content is controlled with an allow list of IP addresses. The <i>"allow_list.txt"</i> file identifies these IP addresses. A separate remove list identifies IP addresses that should no longer have access to this content. I created an algorithm to automate updating the <i>"allow_list.txt"</i> file and remove these IP addresses that should no longer have access. <br />


<h2>Languages and Utilities Used</h2>

- <b>Python</b>
- <b>Linux</b>

<h2>Project Walk-Through:</h2>

<p align="center">
<b>Open the file that contains the allow list</b>
<br/> For the first part of the algorithm, I opened the <i>"allow_list.txt"</i> file. First, I assigned this file name as a string to the <i>import_file</i> variable: <br/>
<br/> <img src="https://i.imgur.com/kzJZsDP.png" height="80%" width="80%" alt=/>
<br/>Then, I used a with statement to open the file:<br/>
<br/> <img src="https://i.imgur.com/qZnkZJg.png" height="80%" width="80%" alt=/>
<br/> In my algorithm, the <i>with</i> statement is used with the <i>.open()</i> function in read mode to open the allow list file for the purpose of reading it. The purpose of opening the file is to allow me to access the IP addresses stored in the allow list file. The <i>with</i> keyword will help manage the resources by closing the file after exiting the <i>with</i> statement. In the code <i>with open(import_file, "r") as file:</i>, the <i>open()</i> function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, <i>"r"</i> indicates that I want to read it. The code also uses the <i>as</i> keyword to assign a variable named <i>file</i>; <i>file</i> stores the output of the <i>.open()</i> function while I work within the with statement. <br/>
<br/>
<b>Read the file contents</b> <br/>
In order to read the file contents, I used the <i>.read()</i> method to convert it into the string.<br/>
<br/> <img src="https://i.imgur.com/wtidMPm.png" height="80%" width="80%" alt=/>
<br/>When using an <i>.open()</i> function that includes the argument <i>"r"</i> for “read,” I can call the <i>.read()</i> function in the body of the <i>with</i> statement. The <i>.read()</i> method converts the file into a string and allows me to read it. I applied the <i>.read()</i> method to the <i>file</i> variable identified in the <i>with</i> statement. Then, I assigned the string output of this method to the variable <i>ip_addresses</i>. <br/>
<br/> In summary, this code reads the contents of the <i>"allow_list.txt"</i> file into a string format that allows me to later use the string to organize and extract data in my Python program.<br />
<p align="center">
<b>Convert the string into a list</b> <br/>
In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the <i>.split()</i> method to convert the <i>ip_addresses</i> string into a list:<br/>
<br /> <img src="https://i.imgur.com/ajLFfiw.png" height="80%" width="80%"alt=/><br />
The <i>.split()</i> function is called by appending it to a string variable. It works by converting the contents of a string to a list. The purpose of splitting <i>ip_addresses</i> into a list is to make it easier to remove IP addresses from the allow list. By default, the <i>.split()</i> function splits the text by whitespace into list elements. In this algorithm, the <i>.split()</i> function takes the data stored in the variable <i>ip_addresses</i>, which is a string of IP addresses that are each separated by a whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable <i>ip_addresses</i>. <br/>
<br/>
<b>Iterate through the remove list</b>  
 <br/>
A key part of my algorithm involves iterating through the IP addresses that are elements in the <i>remove_list</i>. To do this, I incorporated a <i>for</i> loop:<br/>
<br/> <img src="https://i.imgur.com/pkW2PNJ.png" height="80%" width="80%" alt=/>
<br />
The <i>for</i> loop in Python repeats code for a specified sequence. The overall purpose of the <i>for</i> loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The <i>for</i> keyword starts the <i>for</i> loop. It is followed by the loop variable <i>element</i> and the keyword in. The keyword <i>in</i> indicates to iterate through the sequence <i>ip_addresses</i> and assign each value to the loop variable <i>element</i>.<br/>
 <br />
<b>Remove IP addresses that are on the remove list:</b>  
<br/>
 My algorithm requires removing any IP address from the allow list, <i>ip_addresses</i>, that is also contained in <i>remove_list</i>.  Because there were not any duplicates in <i>ip_addresses</i>, I was able to use the following code to do this:<br/>
<br/> <img src="https://i.imgur.com/cHWLqAg.png" height="80%" width="80%" alt=/>
<br />
First, within my <i>for</i> loop, I created a conditional that evaluated whether or not the loop variable <i>element</i> was found in the <i>ip_addresses</i> list. I did this because applying <i>.remove()</i> to elements that were not found in <i>ip_addresses</i> would result in an error.  <br />
<br/> Then, within that conditional, I applied <i>.remove()</i> to <i>ip_addresses</i>. I passed in the loop variable <i>element</i> as the argument so that each IP address that was in the <i>remove_list</i> would be removed from <i>ip_addresses</i>.<br/>
<br/>
<b>Update the file with the revised list of IP addresses</b>  
<br/>
As a final step in my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do so, I first needed to convert the list back into a string. I used the <i>.join()</i> method for this:<br/>
<br/><img src="https://i.imgur.com/fIqU3ly.png" height="80%" width="80%" alt=/>
<br />
The <i>.join()</i> method combines all items in an iterable into a string. The <i>.join()</i> method is applied to a string containing characters that will separate the elements in the iterable once joined into a string. In this algorithm, I used the <i>.join()</i> method to create a string from the list <i>ip_addresses</i> so that I could pass it in as an argument to the <i>.write()</i> method when writing to the file <i>"allow_list.txt"</i>. I used the string <i>("\n")</i> as the separator to instruct Python to place each element on a new line.<br/>
 <br/>
Then, I used another <i>with</i> statement and the <i>.write()</i> method to update the file: <br/>
<br/><img src="https://i.imgur.com/pwAAP91.png" height="80%" width="80%" alt=/>
<br/>
This time, I used a second argument of <i>"w"</i> with the <i>open()</i> function in my <i>with</i> statement. This argument indicates that I want to open a file to write over its contents. When using this argument <i>"w"</i>, I can call the <i>.write()</i> function in the body of the <i>with</i> statement. The <i>.write()</i> function writes string data to a specified file and replaces any existing file content.<br/>
<br/>
In this case I wanted to write the updated allow list as a string to the file <i>"allow_list.txt"</i>. This way, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, I appended the <i>.write()</i> function to the file object <i>file</i> that I identified in the <i>with statement</i>. I passed in the <i>ip_addresses</i> variable as the argument to specify that the contents of the file specified in the <i>with</i> statement should be replaced with the data in this variable.<br/>
<br/>
<b>Summary:</b> <br/>
I created an algorithm that removes IP addresses identified in a <i>remove_list</i> variable from the <i>"allow_list.txt"</i> file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable <i>ip_addresses</i>. I then iterated through the IP addresses in <i>remove_list</i>. With each iteration, I evaluated if the element was part of the <i>ip_addresses</i> list. If it was, I applied the <i>.remove()</i> method to it to remove the element from <i>ip_addresses</i>. After this, I used the <i>.join()</i> method to convert the <i>ip_addresses</i> back into a string so that I could write over the contents of the <i>"allow_list.txt"</i> file with the revised list of IP addresses.<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
