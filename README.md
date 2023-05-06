Download Link: https://assignmentchef.com/product/solved-ece404-homework-4
<br>
In this homework, you will get a deeper understanding of finite fields of the form <em>GF</em>(2<em><sup>n</sup></em>) and the Advanced Encryption Standard.

<strong>IMPORTANT</strong>: For this homework, you will have both a <strong>physical </strong>(i.e. paper hard-copy) and <strong>electronic </strong>submission. The physical submission should be handed in at the front of the classroom on the due date. See the Submission Notes section for details.

<h1>Theory Problems</h1>

<ol>

 <li>Determine the following in GF(11), please show your work:

  <ul>

   <li>(3<em>x</em><sup>4 </sup>+ 5<em>x</em><sup>2 </sup>+ 10) − (8<em>x</em><sup>4 </sup>+ 5<em>x</em><sup>2 </sup>+ 2<em>x </em>+ 1)</li>

   <li>(5<em>x</em><sup>2 </sup>+ 2<em>x </em>+ 7) × (5<em>x</em><sup>3 </sup>+ 3<em>x</em><sup>2 </sup>+ 3<em>x </em>+ 2)</li>

  </ul></li>

 <li>For the finite field <em>GF</em>(2<sup>3</sup>), calculate the following for the modulus polynomial <em>x</em><sup>3 </sup>+ <em>x</em><sup>2 </sup>+ 1, please show your work:

  <ul>

   <li>(<em>x</em><sup>2 </sup>+ <em>x </em>+ 1) × (<em>x </em>+ 1)</li>

   <li>(<em>x</em><sup>2 </sup>+ 1) − (<em>x</em><sup>2 </sup>+ <em>x </em>+ 1)</li>

  </ul></li>

</ol>

<h1>Programming Problem</h1>

Write a script in Python or Perl to implement the AES algorithm with a <u>256-bit </u>key size. The following points may aid you in your implementation and are worth noting:

<ol>

 <li>Each round of AES involves the following:

  <ul>

   <li>Single-byte based substitution</li>

   <li>Row-wise permutation</li>

   <li>Column-wise mixing</li>

   <li>Addition of the round key</li>

  </ul></li>

 <li><strong>The order in which these four steps are executed is different for encryption and decryption. The last round for encryption does not involve the ‘Mix columns’ step. The last round for decryption does not involve the ‘Inverse mix columns’ step.</strong></li>

 <li>As you know, AES has variable key-length, and the number of rounds of processing depend upon the key-length. The lecture assumes the 128-bit key length and all subsequent explanation is based upon that assumption. The key provided to you is 256-bits long and hence there will be a slight variation in how you generate the <em>keyschedule</em>. The following explanation will be helpful in that regard:

  <ul>

   <li>For the key expansion algorithm, note that irrespective of the key-length, each round still uses only 4 words from the <em>keyschedule</em>. Just as we organised the 128-bit key in 4 words for key-expansion, we organise the 256-bit key in 8 words.</li>

   <li>Each step of the key-expansion algorithm takes us from 8-words in one round to 8words in the next round. Hence, 8 such steps will give us a 64-word key schedule. The implementation of the <em>g</em>() function remains the same. The logic of obtaining the 8 words from the <em>j<sup>th </sup></em>step of key-expansion to the (<em>j </em>+ 1)<em><sup>th </sup></em>step also remains the same.</li>

   <li>Note that since the key is 256-bit long, there will be 14 rounds of processing in the AES, plus the initial processing. Because each round of processing uses only 4 words from the <em>keyschedule</em>, you will require only a 60-word <em>keyschedule</em>. However, the previous step generates a 64-word schedule,so you will have to ignore the last 4 words in the schedule.</li>

  </ul></li>

</ol>

<strong>Program Requirements</strong>

Similar to your DES implementation in homework 2, your program should have the following call syntax:

python AES.py -e message.txt key.txt encrypted.txt python AES.py -d encrypted.txt key.txt decrypted.txt

Explanation of the syntax:

For encryption , AES.py reads the input plaintext from message.txt and the key from key.txt, then writes the encrypted output in <strong>hexstring </strong>form to encrypted.txt

For decryption (denoted by -d), read in the ciphertext encrypted.txt in <strong>hexstring </strong>format and save the decrypted output to decrypted.txt.

Make sure when reading the encrypted text during decryption that you convert it to the hex values they represent and not the ASCII characters themselves (i.e. do not simply do <em>BitV ector</em>(<em>filename </em>= <sup>0</sup><em>encrypted.txt</em><sup>0</sup>) without any more processing). You may want to use <em>BitV ector</em>(<em>hexstring </em>= <em>…</em>) instead.

<h1>Notes</h1>

<ul>

 <li>This should go without saying, but <strong>start on this homework early</strong>. This homework is a bit more involved than the previous homeworks.</li>

 <li>On the ECE 404 Homework webpage, we have provided a sample plaintext. We have also provided the results after each of the four steps in the <strong>first round of processing for the first block</strong>. The key used is to get these results is: <em>thepurdueuniversityboilermakers</em>!</li>

 <li>You can check to see if your encryption works properly using the following website (make sure to change the key size and select Hex output) :</li>

</ul>

https://www.devglan.com/online-tools/aes-encryption-decryption

Due to different padding methods for blocks that are not a multiple of the block size, the final block of encryption generated from this website will not match your final encrypted block if you pad zeros from the right. However, the remaining blocks should match.