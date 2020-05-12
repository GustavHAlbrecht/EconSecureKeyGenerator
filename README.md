# EconSecureKeyGenerator
Idea: Combine a human-unique identifier like FirstnameLastnameBirthdateBirthplace and a secret 6-8 decimal digit number. Use the resulting bit sequence to generate a private key. The algorithm to do must be computationally intensive and therefore costly (by using repeated hashing for example). Suppose costs of generating a private key are c. Suppose further the secret number has n decimial digest and therefore the space contains 10^n differnt combinations. Given that an attacker knows the human-unique identifier and assuming secret numbers are uniformly distributed in the space he would have to try (10^n)/2 differnt combinations on average to extract the private key. This would imply cost of (10^n)/2 *c.

<p>Example 1: c= 10$ n= 6 
<br>
Cost to extract private key = (10^6)/2 * 10 $ = 5,000,000 $
<br></p>
<p>Example 2: c= 1$ n= 8
<br>
Cost to extract private key = (10^8)/2 * 1$ = 50,000,000$</p>
<p>Example 3: c=1$ n=6
<br>
Cost to extract private key = (10^6)/2 * 10 $ = 500,000$</p>

