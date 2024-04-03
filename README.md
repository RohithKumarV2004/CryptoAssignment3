
1. A one-way function is a function that is easy to evaluate in one direction, but difficult to compute in the reverse direction. A trapdoor one-way function is a one-way function with an additional property that makes it easy to compute in the reverse direction when some additional information is revealed. This additional information is called the "trapdoor".
2. Proof from notes ig - need to learn
3. Not sure but Keygen of rsa steps: 
	1.   Miller Rabin Test to get prime numbers -> O(k*n^3) (k->iteration)
	2. n = p x q -> O(n^2)
	3. O(1) to find e as you take 3 or 65537
	4. Finding d -> totient computing O(n ^ 3)
		Total -> O(k x n^3)
4.  RSA  p=17 q=31 n=527
	1. C = m^e mod n = 2^7 mod 17x31 = 128
	2.  d = e^-1 mod phi(n) --->     phi(n) = 16x30 = 480  ---> 7^-1 mod 480  ----> -137 mod 480=343
	3.  M  = [ (C <sup>(343 mod 16)</sup> mod 31) x (31 <sup>-1</sup> mod 17) x (31) + 
			(C <sup>(343 mod 30)</sup> mod 17) x (17 <sup>-1</sup> mod 31)x(17)) ] mod 527 
		= [ (2 <sup>1</sup> mod 31) x (-6) x (31) + (2 <sup>1</sup> mod 17) x (11) x (17)]   mod 527  
		= [-372  + 374 ] = 2
		==Note:== C=2^7 which is again modded with p-1 or q-1 due to mod properties
5. Φ(n) = (p-1)(q-1) and n=pq. To find p,q you need to factorise n hence as factorisation of n is hard this is also hard.
6. skill issue
7. Since gcd(e<sub>a</sub>, e<sub>b</sub>) = 1, we can find x,y such that  xe<sub>a</sub>+y e<sub>b</sub>=1
	Now we also know that c<sub>a</sub> = m<sup>e<sub>a</sub></sup> mod n,  c<sub>b</sub> = m<sup>e<sub>b</sub></sup> mod n
	We can take c<sub>a</sub><sup>x</sup> c<sub>b</sub><sup>y</sup>  = m<sup>xe<sub>a</sub>+ ye<sub>b</sub></sup> = m
8. Skip
9. Skip
10. Direct CRT : x ≡ 14387 (mod 17550)
11. Skip
12. Skip
13. Direct CRT then square root ig but its throwing and I think its not there tho
14. So ap + bq = 1 by extended euclidean algo
	- Now a = p<sup>-1</sup> mod q
	- and b = q<sup>-1</sup> mod p
	- So p(p<sup>-1</sup> mod q) + q(q<sup>-1</sup> mod p)  = 1
	- In CRT x ≅ (yp(p<sup>-1</sup> mod q) + yq(q<sup>-1</sup> mod p) ) mod pq ==> x = y mod pq
15. Ski
16. Yes, attacker will have c<sub>i</sub>= m<sup>3</sup> mod n<sup>i</sup> where 1<= i <= 3 . Then by congruence -> m<sup>3</sup> ≅ c<sub>i</sub>mod n<sup>i</sup>
17. It is susceptible to Chosen Plaintext attack as it acts like a block cipher. (Game attacker - challenger)
		Lets say message m is encrypted to cipher as c = m<sup>e</sup>mod n
		 Now it is vulnerable to Chosen Ciphertext attack because we can manipulate the ciphertext by adding extra data to the message
		 Now lets add data "r" to this message
		 c<sub>new</sub> = cr<sup>e</sup>mod n
		 Now with this when c<sub>new</sub> is decrypted  the value is (mr)<sup>e</sup> thus changing the message
		 This is possible when m doesn't fill a complete block as r is added in the empty space (1024 - sizeOf(m)). It can be avoided by using padding
18. Skill issue I have
19. These
    1. Secure as xoring doesnt reveal anything about the message
	2. Not  secure under game-adversary-challenger with m<sub>0</sub> = 0<sup>128</sup> and m<sub>1</sub> = 1<sup>128</sup>
	3. Should be secure 
20. So
	1.  Combinations of  0th bit of MSB = { 0,1 } and 0th bit of LSB = { 0,1 } , 
		1. so (0,0)=0->x value = eve
		2. so (1,0)=1->x value = eve
		3. so (0,1)=1->x value = odd
		4. so (1,1)=1->x value = odd
			(MSB,LSB) above
			Bob answers eve in cases 1 and 4 and odd for 2 and 3 -> probability = 3/4
	2. She can't cheat on the case of  (0,0) ->  probability = 3/4
	3. Combinations of  0th bit of MSB = { 0,1 } and 0th bit of LSB = { 0,1 } , 
		1. so (0,0)=0->x value = eve
		2. so (1,0)=1->x value = eve
		3. so (0,1)=1->x value = odd
		4. so (1,1)=0->x value = odd
			(MSB,LSB) above
			Bob answers eve in cases 1 and 4 and odd for 2 and 3 -> probability = 1/2
		She can cheat on every case as cases are complimentary ->  probability = 1
