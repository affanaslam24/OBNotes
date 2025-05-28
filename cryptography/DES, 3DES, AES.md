We first need to understand [[Fiestel cihper first]]


### DES (Data Encryption Standard)


![[Pasted image 20250527185536.png]]

![[Pasted image 20250527185731.png]]



![[Pasted image 20250527185802.png]]


![[Pasted image 20250527185951.png]]


![[Pasted image 20250527190340.png]]


![[Pasted image 20250527190423.png]]

![[Pasted image 20250527190447.png]]



![[Pasted image 20250527190536.png]]


---

we are skipping the key generation part: just remember that 16 subgeneration keys are generated which uses 64bit keeys, that are passed through permutation box 2 times to first form 56bit keys and then 48bit keys.

---


well be studying DES analysis:

![[Pasted image 20250527191116.png]]


![[Pasted image 20250527191158.png]]


---


des weaknesses:
![[Pasted image 20250527191405.png]]

![[Pasted image 20250527191434.png]]

![[Pasted image 20250527191444.png]]

![[Pasted image 20250527191623.png]]

![[Pasted image 20250527191631.png]]



---


double des:
![[Pasted image 20250527191825.png]]


![[Pasted image 20250527191841.png]]


![[Pasted image 20250527191929.png]]

![[Pasted image 20250527191939.png]]


![[Pasted image 20250527192005.png]]


![[Pasted image 20250527192052.png]]


mim attack.


![[Pasted image 20250527192159.png]]


![[Pasted image 20250527192213.png]]

![[Pasted image 20250527192234.png]]

![[Pasted image 20250527192246.png]]

![[Pasted image 20250527192256.png]]


---

3des
![[Pasted image 20250527192425.png]]


![[Pasted image 20250527192504.png]]



---


AES:


![[Pasted image 20250527193140.png]]


![[Pasted image 20250527193239.png]]

![[Pasted image 20250527193404.png]]

![[Pasted image 20250527193444.png]]

![[Pasted image 20250527193558.png]]

128 bit key will give 4 wards, and we will have to expand it using expansion algo to create 44 wards. why? because there are 10 rounds that will have to be done, each round will require 4 wards of the key, therefore 44wards in total.


important to note: 
each round will have subBytes, shift rows, mix columns, and add round keys, but the last round doesnt has mix column step.

---


structure of each round
![[Pasted image 20250527194006.png]]

![[Pasted image 20250527194129.png]]

![[Pasted image 20250527194248.png]]


![[Pasted image 20250527194341.png]]

during key add, we are xor-ing

---


difference between aes and des

![[Pasted image 20250527194647.png]]

![[Pasted image 20250527194716.png]]



