# Samourai Hexadecimal Dice

Samourai adaptation of hexadecimal dice ('A' value replaced by Samourai logo).

## Printing the dice

Download the [STL file](./sixteen-sided-hexidecimal-die.stl) to print. This is a standard STL file and should work out-of-the-box.

![Photo of the printed hexadecimal die](./printed-die.jpg)
Printed die and pic: H/T [@diogorsergio](https://twitter.com/diogorsergio/status/997898691091582977)

## Watch-only wallet

### From entropy to mnemonic

#### Creating BIP39 entropy

Determine which die represents the high-order bits either by printing the dice in different colors or by always taking the leftmost die thrown as the high-order bits of the byte.

For a 12-word mnemonic, throw the dice 16 times and note down the hexadecimal values produced. This will produce 128 bits of entropy. For 24 words, perform 32 throws for 256 bits of entropy.

#### Converting entropy to BIP39 mnemonic

Use [https://bip32jp.github.io/english/](https://bip32jp.github.io/english/) offline or run a local copy by first downloading from the [repo](https://github.com/bip32JP/bip32JP.github.io).

In the area labeled **Input Your own Entropy**, check the radio button labeled  **Base 16 (0-9,A-F) (For 16-sided dice)**

Type or paste the hexadecimal string in the input field labeled **Input Your own Entropy**.

Just below the area labeled **BIP39 passphrase**, check the radio button that indicates the number of words corresponding to the amount of entropy you have generated.

Click on the button **Generate new phrase**.

Your mnemonic will appear in the input field labeled **BIP39 passphrase**. Make sure that you see the expected number of words.

### From mnemonic to wallet seed

#### Deriving your public keys

Use [https://iancoleman.io/bip39/](https://iancoleman.io/bip39/) offline or run a local copy by first downloading from the [repo](https://samourai.kayako.com/api/v1/articles/46/attachments/601/download).

In the area labeled **BIP39 Mnemonic**, type or paste your space-separated  mnemonic words.

In the area labeled **BIP39 Passphrase (optional)**, type your BIP39 passphrase.

Select the **BIP44** tab and copy the text displayed for **Account Extended Public Key**. It should begin with the letters *xpub*. This is your legacy account *(pay to public key hash, p2pkh)*. Note the first address displayed under **Derived Addresses**.

Select the **BIP49** tab and copy the text displayed for **Account Extended Public Key**. It should begin with the letters *ypub*. This is a segwit account *(pay to witness public key hash wrapped in pay to script hash, p2sh-p2wpkh)*.  Note the first address displayed under **Derived Addresses**.

Select the **BIP84** tab and copy the text displayed for **Account Extended Public Key**. It should begin with the letters *zpub*. This is a segwit account *(pay to witness public key hash, p2wpkh)*.  Note the first address displayed under **Derived Addresses**.

#### Using Sentinel

Sentinel can be downloaded from [Google Play](https://play.google.com/store/apps/details?id=com.samourai.sentinel&hl=en).

When inserting your extended public keys into Sentinel, be sure to provide the **BIP44** extended public key (*xpub*) by tapping on the menu selection **bitcoin wallet via XPUB (BIP44)**, and provide the **BIP49** (*ypub*) and **BIP84** (*zpub*) extended public keys by tapping on the menu selection **bitcoin wallet via Segwit YPUB/ZPUB (BIP49/84)**.

Verify that the first *deposit address* displayed matches the *derived address* that you noted down when you copied the corresponding extended public key.

## Acknowledgements

Thanks to [Chris McCormick](https://github.com/chr15m) for helping with this fork.

![Rendered image of the hexadecimal die](./render.png)

## Original notice:

Hopefully useful for generating private keys and the like. Author gives no guarantee of any statistical properties of the randomness of this die. You probably want to use other sources of entropy in combination with this. You can ensure dice fairness by conducting chi-square test using [instructions](chi2test.md) and playing with your 3D printer setups, materials and etc.

Based on a modified script from [Thingiverse by bwarne](http://www.thingiverse.com/thing:58408/#files).

