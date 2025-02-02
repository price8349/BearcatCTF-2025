# Curly Password

> A modern approach to secure passwords is to use passphrases to create easy to remember and long passwords. A user used this techinque however they picked 3 words from our home page to use separated by underscores ("_"). They also thought it would be funny to wrap it in our slug. The flag is the password. `eb02e84ccdc45f873c633846efa027b4726a9552a7dad42927ec627e929a500d`

We know the password is `BCCTF{word1_word2_word3}`, of which each word is a word from the BearcatCTF home page.

We can simply just use CeWL to get the initial wordlist:
```
$ cewl https://bearcatctf.io -d 1  
CeWL 6.2.1 (More Fixes) Robin Wood (robin@digi.ninja) (https://digi.ninja/)
the
and
BearcatCTF
person
Cyber
...
```

Then, I generated the final wordlist with this script:

```python
x = open("wl.txt", "r")
y = x.readlines()
for i in y:
    for j in y:
        for k in y:
            print("BCCTF{"+i.strip()+"_"+j.strip()+"_"+k.strip()+"}")
```

This wordlist successfully cracked the hash:

```
eb02e84ccdc45f873c633846efa027b4726a9552a7dad42927ec627e929a500d:BCCTF{sponsor_cybersecurity_Innovation}
```