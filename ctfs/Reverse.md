### Private Room  
```262 Solved
Author: abdilahrf  
Point: 10   Difficulties:

Source code attached
```

Isi dari sourcode adalah merupakan ekriptor, dalam penyelesaian soal ini dapat dilakukan dengan cara melakukan bruteforce huruf yang sesuai dengan cipher, untuk mempercepat pengerjaan baiknya melakukan pemetaan kemudian melakukan replace secara analisis lebih memiliki low cost memory dibandingkan dengan melakukan brutefoce perhuruf, namun saya menggunakan cara ke 2
Beikut kode yang saya gunakan

```python
import string

a = string.printable
flag = [233, 129, 9, 5, 130, 194, 195, 39, 75, 229]
f = ""

for i in flag:
	for x in a:
		p = (((ord(x)<<5) | (ord(x) >> 3)) ^ 111) & 255
		if i == p:
			f += chr(ord(x))

print(f)

```

output dari program

```bash
irwanshofwan@x:~/Desktop/workspace$ python solve_room.py
4w3SomeB!T
```
