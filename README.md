# EconSecureKeyGenerator
<strong>Idea:</strong> Combine a human-unique identifier like FirstnameLastnameBirthdateBirthplace and a secret 6-8 digest pin code. Use the resulting bit sequence to generate a private key. The algorithm to do so must be computationally intensive and therefore costly (by using repeated hashing for example). Suppose costs of generating a private key are c. Suppose further the secret pin code has n digest and therefore the pin space contains 10^n differnt pin codes. Given that an attacker knows the human-unique identifier and assuming pin codes are chosen randomly by users the attacker would have to try (10^n)/2 differnt pin codes on average to find the right one.To check if a pin code is the right one the attacker would have to run the algorithm using the pin code and the human-unique identifier. Because he would have to run the algorithm (10^n)/2 times on average until he finds the right pin code this attack would imply cost of (10^n)/2 *c.

<p>Example 1: c= 10$ n= 6 
<br>
Cost to extract private key = (10^6)/2 * 10 $ = 5,000,000.00 $
<br></p>
<p>Example 2: c= 1$ n= 8
<br>
Cost to extract private key = (10^8)/2 * 1$ = 50,000,000.00$</p>
<p>Example 3: c=1$ n=6
<br>
Cost to extract private key = (10^6)/2 * 10 $ = 500,000.00$</p>

<strong>Application:</strong> A typical user will probably hold less than 500,000.00$ in cryptocurrency. For such a user it is reasonable to generate a private key using values from example 3. Advantages: If a user loses his private keys he can easily generate them again if he knows the 6 decimal places long pin code. There is no need to store an seedphrase anywhere. The cost of doing so will be 1$ in this case. An attacker who does not know the secret number will have to invest 500,000.00$ on average to extract the key.
