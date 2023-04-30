Download Link: https://assignmentchef.com/product/solved-cs-3345-data-structures-project-1
<br>
You are going to write a class to implement a set for integers. The <em>Trie data structure </em>will be used to implement the set. Your program will include a main section that reads commands from System.in. See the sample at the end of this spec’.

The Trie will store numeric (integer) keys of up to 30 digits.

The member functions of the Trie class will be:

boolean insert(String s);                                       // String s comprises a decimal integer of up to 30 characters.

// insert returns false if s is already present, true otherwise

boolean isPresent(String s);       // returns true if s is present, false otherwise boolean delete(String s);  // returns true if s was present, false otherwise int membership();            // returns the number of keys in the data structure void listAll();             // list all members of the Trie’s tree in depth first search order

A Trie is a tree of degree 10. The following Trie contains the keys, listed here in DFS order: 3409, 348, 361, 3612, 538, 5387, 54, 542, 5426.

The black Nodes have a boolean variable set to indicate the end of a key value.

Here are the class variables for the class Node:

class Node { boolean terminal; int outDegree; children Node[];

}

Each Node includes an array of 10 references to Node. When a Node is created, all the array elements in that Node will be initialized to null and the outDegree will be set to zero. You may add other variables to the Node class, but do not add a reference to the Node’s parent and do not store a key value in a Node in any form.

In the above Trie, the root node has only two children, corresponding to digit values ’3’ and ’5’, or positions 3 and 5 in the array of references.

A search begins at the root Node and follows the links, one level for each digit in the given key. To find the key “348” we begin with array element 3 in the root Node and, if it is not null, we check element 4 in the array of the second level node. Finally, we check element 8 in the array of the third level Node. If that Node is marked as a key-terminal, we return “true”.

The insert function begins with a search for the given key. If a null reference is found, a sequence of new Nodes is created corresponding to the missing digits of the key ending.

To insert the key “367” to the above Trie, one new node would be added, corresponding to ’7’. This new node would be referenced by the third level Node corresponding to the prefix “36”.

Deletion also begins with a search for the given key. If found, there are two cases. Say we are deleting “361” from the above Trie. Since the terminal character of the given key has children, deletion only requires flipping the boolean variable that indicates the end of a key.

If the key “348” is deleted, the suffix “8” must be unlinked from the third level node. To do this, when recursing out from the end of the given key, remove links to the characters of that key until a Node is found with degree greater than 1, or a terminal node is found.

Your program will read a text file from System.in that contains text commands. In response to each command your program will output one or more lines of text to system.out.

Here are the commands:

N              // Print your name followed by a newline. A 1234        // Insert the key ’1234’

// Print one of the strings “key 1234 inserted” or “key 1234 already exists” // followed by a newline.

D 344                // Delete the key ’344’.

// Print “key 344 deleted” or “key 344 not found” followed by a newline.

S 98765              // Search for the key “98765”.

// Print “key 98765 found” or “key 98765 not found” followed by a newline.

M                              // Print “Membership is N” where N is the number of keys in the Trie

C ka kb kc kd ke // Check the space separated sequence of keys ka, kb, kc, kd, ke, … // up to the end of the line for presence in the Trie and only list those that are // not present, one per line, each in format “Key kx not found”.

// The keys in the list may each be up to 30 characters long and the input line may // be up to 200 characters long.

L                                           // Print a list of all the elements of the Trie in depth first search order, one key per line.

E                        // The end of the input file

Here are sample input and output data files:

<table width="367">

 <tbody>

  <tr>

   <td width="237">Sample Input</td>

   <td width="130">Output for Sample Input</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">————</td>

   <td width="130">————–</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">N</td>

   <td width="130">Ivor Page</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 123</td>

   <td width="130">Key 123 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 2143</td>

   <td width="130">Key 2143 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 4532</td>

   <td width="130">Key 4532 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 123</td>

   <td width="130">Key 123 already exists</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 2415</td>

   <td width="130">Key 2415 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 26145</td>

   <td width="130">Key 26145 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 12</td>

   <td width="130">Key 12 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 38</td>

   <td width="130">Key 38 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 24</td>

   <td width="130">Key 24 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 45</td>

   <td width="130">Key 45 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 38</td>

   <td width="130">Key 38 already exists</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 453</td>

   <td width="130">Key 453 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 26</td>

   <td width="130">Key 26 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 261457</td>

   <td width="130">Key 261457 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 261</td>

   <td width="130">Key 261 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 2614</td>

   <td width="130">Key 2614 inserted</td>

   <td width="11"> </td>

  </tr>

  <tr>

   <td width="237">A 7755</td>

   <td colspan="2" width="141">Key 7755 inserted</td>

  </tr>

  <tr>

   <td width="237">A 145</td>

   <td colspan="2" width="141">Key 145 inserted</td>

  </tr>

  <tr>

   <td width="237">M</td>

   <td colspan="2" width="141">Membership is 16</td>

  </tr>

  <tr>

   <td width="237">D 26</td>

   <td colspan="2" width="141">Key 26 deleted</td>

  </tr>

  <tr>

   <td width="237">D 26145</td>

   <td colspan="2" width="141">Key 26145 deleted</td>

  </tr>

  <tr>

   <td width="237">D 261457</td>

   <td colspan="2" width="141">Key 261457 deleted</td>

  </tr>

  <tr>

   <td width="237">D 145</td>

   <td colspan="2" width="141">Key 145 deleted</td>

  </tr>

  <tr>

   <td width="237">D 2415</td>

   <td colspan="2" width="141">Key 2415 deleted</td>

  </tr>

  <tr>

   <td width="237">S 241</td>

   <td colspan="2" width="141">Key 241 not found</td>

  </tr>

  <tr>

   <td width="237">S 38</td>

   <td colspan="2" width="141">Key 38 found</td>

  </tr>

  <tr>

   <td width="237">S 2415</td>

   <td colspan="2" width="141">Key 2415 not found</td>

  </tr>

  <tr>

   <td width="237">D 145</td>

   <td colspan="2" width="141">Key 145 not found</td>

  </tr>

  <tr>

   <td width="237">S 6194</td>

   <td colspan="2" width="141">Key 6194 not found</td>

  </tr>

  <tr>

   <td width="237">S 85588537129</td>

   <td colspan="2" width="141">Key 85588537129 not found</td>

  </tr>

  <tr>

   <td width="237">M</td>

   <td colspan="2" width="141">Membership is 11</td>

  </tr>

  <tr>

   <td width="237">S 6194</td>

   <td colspan="2" width="141">Key 6194 not found</td>

  </tr>

  <tr>

   <td width="237">S 6174</td>

   <td colspan="2" width="141">Key 6174 not found</td>

  </tr>

  <tr>

   <td width="237">S 7745</td>

   <td colspan="2" width="141">Key 7745 not found</td>

  </tr>

  <tr>

   <td width="237">S 67677</td>

   <td colspan="2" width="141">Key 67677 not found</td>

  </tr>

  <tr>

   <td width="237">C 38 145 8124 8888</td>

   <td colspan="2" width="141">Key 145 not found</td>

  </tr>

  <tr>

   <td width="237">C 9124 145 85588537129 1111 2222</td>

   <td colspan="2" width="141">Key 8124 not found</td>

  </tr>

  <tr>

   <td width="237">L</td>

   <td colspan="2" width="141">Key 8888 not found</td>

  </tr>

  <tr>

   <td width="237">E</td>

   <td colspan="2" width="141">Key 9124 not foundKey 145 not foundKey 85588537129 not foundKey 1111 not foundKey 2222 not found121232143242612614384545345327755</td>

  </tr>

 </tbody>

</table>

<strong>RULES FOR PROGRAMMING AND SUBMISSION:</strong>

<ol>

 <li>Your submitted code must be entirely your own, except for any code that you copy from this specification.</li>

 <li>Write your program as ONE source file and do not use the “package” construct in your Java source.</li>

 <li>Name your source file as <em>N</em><sub>1</sub><em>N</em><sub>2</sub><em>F</em><sub>1</sub><em>F</em><sub>2</sub>java where your given name begins with the characters <em>N</em><sub>1</sub><em>N</em><sub>2 </sub>and your family name begins with the characters <em>F</em><sub>1</sub><em>F</em><sub>2</sub>. For example my name is Ivor Page, so my source file will be called IVPAP1.java. Note that in all but the “java” extension, all characters are upper case.</li>

 <li>Your program must not output any prompts. Its output must exactly match the format of the <strong>Sample Output </strong></li>

 <li>Do not use any Java Collection Classes, except the arrays to store references in each node. Strings areallowed for input of command lines.</li>

 <li>YOUR PROGRAM MUST READ FROM System.in AND OUTPUT TO System.out. See the examplebelow</li>

 <li>Use good style and layout and comment your code well.</li>

 <li>Use the test files provided on the eLearning webpage for this class to test your program. Sample inputand corresponding output files will be given.</li>

 <li>Submit your ONE source code file to the eLearning Assignment Dropbox for this project. Don’t submita compressed file. Don’t submit a .class file.</li>

 <li><strong>There will be a 1% penalty for each minute of lateness, up to 60 minutes. After 60 minutes of lateness a grade of zero will be recorded.</strong></li>

</ol>

<strong>Sample Sketch of main section</strong>

You don’t have to follow this exactly. You might read entire lines and use the String.split() function.

public static void main( String [ ] args )

{

Trie tre = new Trie();

Scanner in = new Scanner(System.in); boolean notDone = true;

while(notDone) {                                                      // read commands and obey them

String command = in.next(); char com = command.charAt(0); switch(com) { case ’N’: {

System.out.println(“Ivor Page”); break;

}

case ’A’: {                                            // insert

String toAdd = in.next(); if(tre.insert(toAdd)) {

System.out.println(“Key ” + toAdd + ” inserted”);

} else

System.out.println(“Key ” + toAdd + ” already exists”); break;

}

case ’D’: { // delete . . .