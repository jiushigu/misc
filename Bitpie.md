Bitpie is an integrated blockchain asset service product. Its main functions include: sending and receiving, buying and selling, speeding up transactions, exchanges and so on. Currently the most popular mobile digital currency wallet in china which support multi-crypto currencies .

After a brief analysis of the bitpie app (android and ios up to version 3.2.4), we discovered that bitpie actually stored all of the user's digital currency initial keys in plain text.

When bitpie frist startup, it will randomly generate an initial entropy of 128 bits, and then it will expand the 128-bits entropy into 132-bits and generate 12 words to help user to remember the random bits.

The android bither saves the user's initial 128-bits entropy in plain text in the file /com.biepie/shared_prefs/com.bitpie_preferences.xml.Even if the user sets a password, the file is still not encrypted.

Where \<string name="seedPhraseEntropy"\>0b506e43a5f4a53b8a370984dfb0ec89\</string\> is the initial entropy. According to the initial entropy we can easily recover my 12 mnemonics : area lock movie episode engage oven churn thrive luggage work depth because


Also in file /com.biepie/shared_prefs/com.bitpie_preferences.xml, \<string name="seed"\>b8409639eba3c15499e66aaa043ac0f512a49adce99be828d405147533c60a5b5c3a7351a27cf05c144f08d5ad761d7c8642deeb5235a867ebfb0d0b09608ec8\</string\>  is actually the user’s seedkey. Which can used to derive the user's root keys for all of his digital cryptocurrencies. 

The ios version of bitpie have the some problem. There is a plist file in app data folder. And it contains 
\<key\>seedKey\</key\>
	\<string\>889183F3C372B41CAE4025A101FA0022D774719FEF54F4E91D8C1EA3836710C41A1B434F1814A72C6A4AC2C16E567BA01FA91E33F7A73C01709B5DB453AF10E7\</string\>
Which is the seedKey in plaintext.


If a attacker have the root privilege in android or ios file. He can simple read those files and stole all user’s coins.
