Download Link: https://assignmentchef.com/product/solved-cs31-project-4-string-arrays
<br>
<p id="yui_3_17_2_1_1595141673874_46"><span class="">As you gain experience with arrays, you’ll discover that many applications do the same kinds of things with them (e.g., find where an item is in an array, or check whether two arrays differ). You’ll find that it’s helpful to have a library of useful functions that manipulate arrays. (For our purposes now, a library is a collection of functions that developers can call instead of having to write them themselves. For a library to be most useful, the functions in it should be related and organized around a central theme. For example, a screen graphics library might have functions that allow you to draw shapes like lines and circles on the screen, move them around, fill them with color, etc. In this view, the Standard C++ library is really a collection of libraries: a string library, a math library, an input/output library, and much more.)</span>




<span class="">Your assignment is to produce a library that provides functions for many common manipulations of arrays of strings. For each function you must write, this specification will tell you its interface (what paramet</span><span class="">ers it takes, what it returns, and </span><em><span class="">what</span></em><span class=""> it must do). It’s up to you to decide on the implementation (</span><em><span class="">how</span></em><span class=""> it will do it).</span>

The source file you turn in will contain all the functions and a main routine. You can have the main routine do whatever you want, because we will rename it to something harmless, never call it, and append our own main routine to your file. Our main routine will thoroughly test your functions. You’ll probably want your main routine to do the same. If you wish, you may write functions in addition to those required here. We will not directly call any such additional functions. If you wish, your implementation of a function required here may call other functions required here.<span class=""> </span>













<span class="">The program you turn in must build successfully, and during execution, no function (other than main) may read anything from </span><code><span class="">cin</span></code><span class=""> or write anything to </span><code><span class="">cout</span></code><span class="">. If you want to print things out for debugging purposes, write to </span><code><span class="">cerr</span></code><span class=""> instead of </span><code><span class="">cout</span></code><span class="">. When we test your program, we will cause everything written to </span><code><span class="">cerr</span></code><span class=""> to be discarded instead — we will never see that output, so you may leave those debugging output statements in your program if you wish.</span>

<p id="yui_3_17_2_1_1595141673874_50"><span id="yui_3_17_2_1_1595141673874_49" class="">All of the functions you must write take at least two parameters: an array of strings, and the number of items the function will consider in the array, starting from the beginning. For example, in</span>

<span class=""> string folks[8] = {</span><span class=""> “samwell”, “jon”, “margaery”, “daenerys”,</span><span class=""> “tyrion”, “sansa”, “llewmas</span><span class="">“, “noj” }; bool b = hasReverse( folks, 5 ); // should return false and not inspect the last three elements….</span> <span class="">even though the array has 8 elements, only the first 5 had values we were interested in for this call to the function; the function must not examine any of the others. </span>

<span class="">The one error your function implementations don’t have to handle (because they cannot) is when the caller of the function lies and says the array is bigger than it really is. For example, in this situation. the function can’t possibly know the caller is lying about the number of items in the array: </span><span class=""> string people[5] = { “jon”, “mamabbcc!”, “samwell,”, “daenerys.”, “tyrion” }; </span> bool b = hasReverse(people, 25 ); // Bad driver code call // your implementation doesn’t have to check for this, because it can’t

<span class="">T</span><span class="">o make your life easier, whenever this specification talks about strings being equal or about one string being less than or greater than another, the case of letters matters. This means that you can simply use comparison operators like == or &lt; to compare strings. Because of the character collating sequence, all upper case letters come before all lower case letters, so don’t be surprised by that result. The </span><a href="http://web.cs.ucla.edu/classes/spring15/cs31/stahl/Projects/4/faq.html"><span class="">FAQ</span></a><span class=""> has a note about string comparisons.</span>




<h3><b><span class="">Your task</span></b></h3>

<span class="">Here are the functions you must implement:         </span>

<dl id="yui_3_17_2_1_1595141673874_62">

 <dd id="yui_3_17_2_1_1595141673874_61">

  <b><span class="">int</span><span class=""> locateMinimum( </span><span class="">const</span><span class=""> </span><span class="">string</span><span class=""> </span><span class="">array[ ], </span><span class="">int</span></b><b><span class=""> n );</span></b><span class="">Return the index of the smallest item found in the passed array or -1 if n &lt;= 0.  </span><span class="">For example, for the array </span><span class="">people[ 5 ]</span><span class=""> shown above, </span><span class=""><del>locateMaximum</del> locateMinimum( people, 5 )</span><span class=""> should return the value 3, corresponding to the index of “daenerys.”.  If there are multiple duplicate minimum values, return the smallest index that has this minimum value.  The minimum value is determined by its dictionary-sorted order which is what &lt; and &gt; use in C++ to determine true and false.</span>




  <p id="yui_3_17_2_1_1595141673874_59"><b><span class="">int</span><span class=""> countPunctuation( </span><span class="">const</span><span class=""> </span><span class="">string</span><span class=""> array[ ], </span><span class="">int</span><span class="">  </span><span class="">n );</span></b><span id="yui_3_17_2_1_1595141673874_58"><span class="">Return the number of punctuation characters found inside each of the elements of the passed array or if n &lt;= 0 return -1</span><span class="">.  Punctuation characters to be counted should include:   ,   .   ;  –   ?  !   :  ”  (   )     namely, comma, period, semicolon, dash, question mark, exclamation mark, colon, double quote and parentheses.  </span><span class="">For example, for the array </span><span class=""> </span><span class="">people[ 5 ]</span><span class=""> </span><span class=""> shown above, </span><span class="">countPunctuation( people, 5 )</span><span class=""> </span><span id="yui_3_17_2_1_1595141673874_57"><span class=""> should return </span><span class="">3</span><span class="">.   </span><span class="">For the array </span><span class=""> </span><span class="">people[ 5 ]</span><span class=""> </span><span class=""> shown above, </span><span class=""> </span><span class="">countPunctuation( people, 1 )</span><span class=""> </span><span id="yui_3_17_2_1_1595141673874_56"><span class=""> should return </span><span id="yui_3_17_2_1_1595141673874_55"><span class="">0 </span><span class="">because the first element has no punctuation characters. </span></span></span></span></span>

  <b><span class="">bool hasReverse( </span><span class="">const</span><span class=""> </span><span class="">string</span><span class=""> array[ ], </span><span class="">int</span><span class=""> n</span><span class=""> );</span></b><span class="">If there is an element in the passed array whose value is the reverse of an existing value found in the array, return true otherwise false or if n &lt;= 0 return false .  For example, for the array people[ 5 ] shown above, hasReverse( people, 5 ) should return false.  For example, for the array folks[ 8 ] shown above, hasReverse( folks, 8 ) should return true  because “samwell” and its reverse “llewmas” are in the array as well as “jon” and “noj”.</span>

  <b><span class="">char highestOccurredCharacter( const </span><span class="">string</span><span class=""> array[ ], </span><span class="">int</span><span class=""> n, </span><span class="">int</span><span class=""> index</span><span class=""> );</span></b><span class="">For the element found at position index in the passed array, return the character that occurred more frequently than any other character in the identified string element.  Unlike the other functions in this assignment, your code should only inspect a single string, not an entire array.  If multiple characters occur an identical number of times, your function can decide which of these characters to return.  For example, for the array people[ 5 ] shown above, highestOccurredCharacter( people, 5, 0 ) can return either ‘j’ or ‘o’ or ‘n’.  For example, for the array people[ 5 ] shown above, highestOccurredCharacter( people, 5, 2 ) should return ‘l’.</span><span class="">  </span><span class="">If n &lt;= 0 or index &gt;= n or index &lt; 0, return ‘ ’ which is the NULL character.  </span>

  <b><span class="">bool</span><span class=""> isInIncreasingOrder( </span><span class="">const</span><span class=""> </span><span class="">string</span><span class=""> array[ ], </span><span class="">int</span><span class="">  </span><span class="">n );</span></b><span class="">If every value in the array is larger than the one that precedes it, return </span><span class="">true</span><span class=""> </span><span class=""> otherwise </span><span class="">false</span><span class=""> or if n &lt;= 0 return </span><span class="">false</span><span class=""> </span><span class="">.  </span><span class="">For example, for the array </span><span class=""> </span><span class="">people[ 5 ]</span><span class=""> shown above, </span><span class="">isInIncreasingOrder( people, 5 ) should return </span><span class="">false</span><span class="">.  For example, for the array people[ 5 ] shown above, isInIncreasingOrder( people, 3 ) should return true.</span>

 </dd>

 <dd>

  <span class=""><b>char firstNonRepeatedCharacter( const string array[ ], int n, int index );</b>For the element found at position index in the passed array, return the first non-repeated character found in the identified string element.  Unlike the other functions in this assignment, your code should only inspect a single string, not an entire array.  For example, for the array people[ 5 ] shown above, firstNonRepeatedCharacter( people, 5, 1 ) should return ‘!’.  For example, for the array people[ 5 ] shown above, firstNonRepeatedCharacter( people, 5, 0 ) should return ‘j’.  If n &lt;= 0 or index &gt;= n or index &lt; 0, return ‘ ’ which is the NULL character.  </span>

 </dd>

 <dd>

  <span class=""><b>bool isOnlyDigits( const string array[ ], int n );</b></span>If every element in the passed array is comprised of only digit characters 0-9, return <span class="">true</span> otherwise <span class="">false</span> or if n &lt;= 0 return <span class="">false</span>.   An example of using this function is shown below.







 </dd>

 <dd>

  Additionally, I have created a testing tool called CodeBoard to help you check your code.  CodeBoard enables you to be sure you are naming things correctly by running a small number of tests against your code.  Passing CodeBoard tests is not sufficient testing so please do additional testing yourself.  To access CodeBoard for Project 4, please click the link you see in this week named CodeBoard for Project 4.  Inside the file named user_functions.cpp, copy and paste your implementation of the assigned functions.  CodeBoard uses its own main( ) to run tests against your code.  Click Compile and Run.  However please be aware that no editing changes can be saved inside CodeBoard.  In this anonymous user configuration, CodeBoard is read-only and does not allow for saving changes.

 </dd>

</dl>

<dl>

 <dd>

  <p class="p1"><b><span class="">Programming Guidelines</span></b>

 </dd>

</dl>

<span class="">Your program must <em>not</em> use any function templates from the algorithms portion of the Standard C++ library or use STL &lt;list&gt; or &lt;vector&gt;. If you don’t know what the previous sentence is talking about, you have nothing to worry about. Additionally, your code must <i>not</i> use any global variables which are variables declared outside the scope of your individual functions.</span>

<span class="">Your program must build successfully under both Visual C++ and either clang++ or g++.</span>

<span class="">The correctness of your program must not depend on undefined program behavior. Your program could not, for example, assume anything about </span><code><span class="">t</span></code><span class="">‘s value in the following, or even whether or not the program crashes:</span>

<pre>	int main()	{	    string s[3] = { "samwell", "jon", "tyrion" };	    string t = s[3];  // position 3 is out of range	    …</pre>

<span class="">What you will turn in for this assignment is a zip file containing these two files and nothing more:</span>

<ol>

 <li><span class="">A text file named </span><b><span class="">array.cpp</span><span class=""> </span></b><span class=""> that contains the source code for your C++ program. Your source code should have helpful comments that explain any non-obvious code.</span></li>

 <li><span class="">A file named </span><strong><span class="">report.doc</span></strong><span class=""> </span><span class="">or </span><strong><span class="">report.docx</span></strong><span class=""> (in Microsoft Word format) or </span><strong><span class="">report.txt</span></strong><span class=""> (an ordinary text file) that contains in addition </span><b><span class="">your name</span></b><span class=""> and </span><b><span class="">your UCLA Id Number</span></b><span class="">:</span>

  <ol>

   <li><span class="">A brief description of notable obstacles you overcame.</span></li>

   <li><span class="">A list of the test data that could be used to thoroughly test your functions, along with the reason for each test. You must note which test cases your program does not handle correctly. (This could happen if you didn’t have time to write a complete solution, or if you ran out of time while still debugging a supposedly complete solution.) Notice that most of this portion of your report can be written just after you read the requirements in this specification, before you even start designing your program.</span></li>

  </ol></li>

</ol>

<span class="">How nice! Your report this time doesn’t have to contain any design documentation.</span>

<span class="">As with Project 3, a nice way to test your functions is to use the </span><code><span class="">assert</span></code><span class=""> facility from the standard library. As an example, here’s a very incomplete set of tests for Project 4:</span>

<pre>	#include &lt;iostream&gt;	#include &lt;string&gt;	#include &lt;cassert&gt;	using namespace std;   	int main()	{</pre>

<p class="p1"><span class="s1"> string a[6] = { </span>“123”, “456”, “789”, “gamma”, “beta”, “delta” };

<p class="p1"><span class="s1">    </span><span class="s2">assert</span><span class="s1">(isOnlyDigits</span><span class="s1">(a, 6</span><span class="s1"> ) == false</span><span class="s1">); </span><span class="s2"> assert</span><span class="s1">(</span><span class="s3">isOnlyDigits</span><span class="s1">(a, 3</span><span class="s1"> ) == true</span><span class="s1">);</span>

<pre>	    cout &lt;&lt; "All tests succeeded" &lt;&lt; endl;            return( 0 );</pre>

<pre>         }</pre>

<span class="">The reason for the one line of output at the end is to ensure that you can distinguish the situation of all tests succeeding from the case where one test silently crashes the program.</span>

<span class="">Make sure that if you were to replace your main routine with the one above, your program would build successfully under both Visual C++ and either clang++ or g++.  This means that even if you haven’t figured out how to implement some of the functions, you must still have </span><em><span class="">some</span></em><span class=""> kind of implementations for them, even if those implementations do nothing more than immediately return. </span>

<span class="">By July 27, there will be links on the class webpage that will enable you to turn in your zip file electronically. Turn in the file by the due time above. Give yourself enough time to be sure you can turn something in, because we will not accept excuses like “My network connection at home was down, and I didn’t have a way to copy my files and bring them to a SEASnet machine.” There’s a lot to be said for turning in a preliminary version of your program and report early (You can always overwrite it with a later submission). That way you have something submitted in case there’s a problem later.</span>




<dl>

 <dd>

  <b>G31 Build Commands</b>

 </dd>

</dl>

<pre>	g31 -c array.cpp        g31 array.o -o runnable        ./runnable</pre>