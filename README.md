# eyeware 𝄐

[Diceware](http://world.std.com/~reinhold/diceware.html) is a popular password-generation method using random selections from a list of ~8000 words. Although there exists a standard Diceware list, any sufficient collection of unique words will do. eyeware is an **alternative Diceware list** consisting entirely of words found in Tolkien's *The Lord of the Rings*.

## I just want to generate a password in my Linux terminal now!

First, run the following command to download `eyeware8k` (the word list for passphrase generation on a computer):

```
wget https://raw.githubusercontent.com/nightsense/eyeware/master/eyeware8k -O /tmp/eyeware8k
```

Then, to generate a 7-word passphrase, run:

```
shuf --random-source=/dev/random -r -n 7 < /tmp/eyeware8k
```

If the password generation process hangs, it's probably waiting for entropy; try moving the mouse around.

Change the number `7` in the above command to change the passphrase length. A 7-word passphrase can be regarded as the current "gold standard" for practical personal security, given that once a Diceware passphrase reaches 7 words, it becomes "[unbreakable](http://world.std.com/~reinhold/dicewarefaq.html#howlong) with any known technology".

## how eyeware was made (*The Forging of the List*)

The standard Diceware list consists mostly, but not entirely, of words composed with the lowercase English alphabet. eyeware elevates this tendency to a strict standard: in preparing the word list, capitals were converted to lowercase, diacritics were removed, and words containing non-letter glyphs (such as apostrophes or hyphens) were dropped. Additionally, word length was limited to 3-9 characters.

Subject to these filters, all words that appear two or more times in *The Lord of the Rings* were placed in the eyeware word list. Single-occurence words were then added, in alphabetical order, until the goal word total was reached.

## how to generate a passphrase (*The Five Dice*)

To generate a passphrase with a Diceware word list (see the [official site](http://world.std.com/~reinhold/diceware.html) for full instructions):

- roll five dice (or one die five times) and read them left to right to get a 5-digit number
- find the corresponding word on the list (such as the [original Diceware list](http://world.std.com/~reinhold/dicewarewordlist.pdf) or the [eyeware list](https://github.com/nightsense/eyeware/blob/master/eyeware-wordlist))
- repeat until the desired number of words is reached
- use the words, in the order they were generated and with spaces between them, as the passphrase

For instance, the passphrase might be: `toby hew aught neighed rumoured spies son`.

It may be tempting to alter the passphrase to make it more memorable. **Do not remove or reorder any words or characters**, for it will compromise the randomness (and therefore security) of the phrase.

One approach to memorizing the passphrase is to add "connecting words" that make the phrase sound more natural.

`toby [didn't] hew aught [and] neighed [that it was] rumoured [that he] spies [on his] son`

By adding these words when reciting the passphrase in one's head, but not actually adding them to the typed passphrase, memorization can be eased without increasing the characters to be typed.

## computer-generation of passphrases (*The Randomness of the Computer*)

Alternatively, one can generate a passphrase [using a computer](http://world.std.com/~reinhold/dicewarefaq.html#computer). The Diceware author recommends using a slightly longer list (8192 words, to make it a whole power of two; for there is only one Lord of the RNG...and he does not share power) for computer generation. The file [`eyeware8k`](https://github.com/nightsense/eyeware/blob/master/eyeware8k) was created for this purpose.

**Many methods of random number generation are insufficiently random for strong passphrase generation. Be sure to choose a quality source of randomness, such as [`shuf --random-source=/dev/random`](https://wiki.archlinux.org/index.php/Random_number_generation) on a Linux system.**
