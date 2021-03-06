# EconSecureKeyGenerator
<strong>Idea:</strong> Combine a human-unique identifier like FirstnameLastnameBirthdateBirthplace that acts a source of randomness and a secret 6-8 digest pin code.Recursively  hash this bit sequence(using SHA256 for example) where the output of the last hash is the input of the next hash similiar to a VDF. SHA256 will output a 256 bit sequence which is essentially a private key. Depending on the number of hashes the algorithm to generate this private key can be made arbitrary costly. 
<br>
<p>Key = H(...H((H(H(FirstnameLastnameBirthdateBirthplace + secret pin code)))..).</p>
<br>
Suppose costs of generating a private key are c. Suppose further the secret pin code has n digest and therefore the pin space contains 10<sup>n</sup> differnt pin codes. Given that an attacker knows the human-unique identifier and assuming pin codes are chosen randomly by users the attacker would have to try (10<sup>n</sup>)/2 differnt pin codes on average to find the right one.To check if a pin code is the right one the attacker would have to run the algorithm using the pin code and the human-unique identifier. Because he would have to run the algorithm (10<sup>n</sup>)/2 times on average until he finds the right pin code this attack would imply cost of (10<sup>n</sup>)/2 *c.

<p>Example 1: c= 10$ n= 6 
<br>
Cost to extract private key = (10<sup>6</sup>)/2 * 10 $ = 5,000,000.00 $
<br></p>
<p>Example 2: c= 1$ n= 8
<br>
Cost to extract private key = (10<sup>8</sup>)/2 * 1$ = 50,000,000.00$</p>
<p>Example 3: c=1$ n=6
<br>
Cost to extract private key = (10<sup>6</sup>)/2 * 10 $ = 500,000.00$</p>

<strong>Application:</strong> A typical user will probably hold less than 500,000.00$ in cryptocurrency. For such a user it is reasonable to generate a private key using values from example 3. Advantages: If a user loses his private keys he can easily generate them again if he knows the 6 decimal places long pin code (an his FirstnameLastnameBirthdateBirthplace). There is no need to store a seedphrase anywhere. The cost of doing so will be 1$ in this case. An attacker who does not know the secret number will have to invest 500,000.00$ on average to extract the key. No rational attacker will perform such an attack when the average costs are much higher than the average profit. Essentially what is happening we reduce the initial key space(to a secret 6-8 digest pin code) which allows for useres to memorize keys but make the real private key creation from this initial key space costly and therefore practically secure. To have uniqe initial inputs and therefore a unique private key we simply add a source of randomness like FirstnameLastnameBirthdateBirthplace that you know by default.  

<strong>Assumptions:</strong>
<ol>
  <li>Secret pin codes must be chosen randomly from the pin code space by users. Otherwise an attacker can exploit heuristics and the average trials to find the right pin code will be less than (10<sup>n</sup>)/2.  </li>
  <li> The costs c of running the algorithm must be the same for everbody. Using repeated hashing where the previous hash is the input to the next hash function reduces parallel execution. Probably holding up to this assumption will require application specific machines by third partys running the repeated hashing. </li>
  <li> The algorithm is a mapping from the combination of the human-unique identifiers and the secret pin code to the private key space. For two differnt persons every possible private key in the private key space must be equally probable.</li>
 </ol>
