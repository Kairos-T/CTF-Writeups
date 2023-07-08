# Magnet Virtual Summit CTF 2023

Background: Magnet Virtual Summit CTF 2023 by Magnet Forensics took place in March 2023, and I unfortunately missed it. However, the challenge questions are still available from Magnet Forensics, and I am going to try it :D



## Cipher Challenges

### 1. Time to practice our CW.

{% code overflow="wrap" %}
```
-.- . -.– —... .–. .. -. . .- .–. .–. .-.. . — -. .–. .. –.. –.. .
```
{% endcode %}

This looks like morse code to me, but to be safe, I still chucked the string to [dcode.fr's cipher identifier too](https://www.dcode.fr/cipher-identifier)l which did confirm that it was a morse code cipher.&#x20;

dcode.fr also did provide with the [morse code translator](https://www.dcode.fr/morse-code), which gave the flag:&#x20;

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Flag: "KEY:PINEAPPLEONPIZZAISGREAT!"

### 2. Time to return to the bas(e)ics and eat a salad .

```
TFk6THBLeHFqdWJMcEt4cWp1Yg==
```

This was a clear Base64 encrypted text because of the "==" at the end, plus the hint in the question itself - base(e)ics.&#x20;

I used a [Base64 decoder](https://www.base64decode.org/) to decrypt this:

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

I was a little confused by the gibberish at first, but the question did include "salad", which seemed to provide a clue to caesar cipher. Entering that string into [dcode.fr's caesar cipher decoder](https://www.dcode.fr/caesar-cipher) effectively helped me get the flag:&#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Flag: IV:ImHungryImHungry

### 3. I understood math till they started adding letters.

{% code overflow="wrap" %}
```
(23492930345809345834905890346890456890456804586 + 53453489824379894375555555555555555555555555555555555555555555553894792 / 234890390458349056748396748957698473586974589 * Y) + (23499596346045645896745988623904893753894679834579384579 / o * 2342342342346782025720570023) * u + 34502750923508934758932475898923025027590823759023758932750970789 * (r + e * (1834918237981237469812376491236491263478932176478231647823634789612) / ((203485739804856783474658394753498 – D + 8299578904356797823459238459823476592348759342) * 9827438923465897236498273493 / o + 2394573904853495793847534 – i * (23423489928937498384798 * n) + 392874982374982374983 * g) * (23893473920589267658972347 + G + 520938752348909023423904783490752345734928576 – r – 23498023849234789236723896329784692387 + 234234283746823746782365 / a) = te
```
{% endcode %}

Okay. This one really stumped me. I knew this looked like RSA encryption,  but there wasn't enough information for me to break it   or retrieve any flag. But wait.. why are there so many unknown variables??

The variables looked a bit weird, and upon close inspection, the flag was just pulling out the letterss from the whole equation :clap:.

Flag: YoureDoingGreat



### 4.  I can’t remember that URL. I wish I could rewind my day and bookmark it!

{% code overflow="wrap" %}
```
442%3Dt%3FwcVmRcN%2DKj9%2Feb%2Eutuoy%2F%2F%3Asptth
```
{% endcode %}

Since "URL" is mentioned in the question, I looked for a URL decoder. [Cyberchef](https://gchq.github.io/CyberChef/) has a pretty neat tool for this.&#x20;

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Putting it through the tool seemed to return a URL but reversed. I simply dragged the "Reverse" tool from Cyberchef into the 'recipe' to reverse the text to get the flag. \
\
Flag: "[https://youtu.be/9jK-NcRmVcw?t=244](https://youtu.be/9jK-NcRmVcw?t=244)"&#x20;

### 5. i Am Excited for thiS year’s ctf, no cap(s)

{% code overflow="wrap" %}
```
fc52c3f2c74e4f3e745a9042f283c46a28060ea71ec21424ab09c98092fe5efae7f99267a5c5ac55ad8b8e89b0ded9cc
```
{% endcode %}

Looking at the question, the letters that are capitalised are A, E and S, which points to the AES encryption method.

Cyberchef does have a tool for AES Decryption too, but I still required a Key and Initialisation vector (IV). But those sound familiar... they were the flags to the previous questions!

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

Or... not. I am back to being stumped! I had to take many looks at this question to solve it, but I realised the hint was "no cap(s)". So I made all the letters in both the Key and IV lowercase and:&#x20;

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

I got the flag after changing HEX to UTF8 too.&#x20;

Flag: "[https://www.youtube.com/watch?v=xm3YgoEiEDc](https://www.youtube.com/watch?v=xm3YgoEiEDc)"

If you clicked on the link, congrats :)

But anyway, that is it for the cipher challenges.



## iOS Challenges

For the iOS Challenges, the logical data file can be downloaded [here](https://go.magnetforensics.com/e/52162/41A1130001E-files-full-001-zip/lhmdf2/1324250137?h=VjIef9nVy7wB1qONdAWbDcVEBzeNtFMM\_Ou-e\_OJSOw) (MD5: **067606649297d7adcf6082e5ed0acbb9**).

I used [iLEAPP](https://github.com/abrignoni/iLEAPP), a free tool to analyse iOS logs and events. Just like the android challenges from Magnet User Summit CTF 2023, this was my first time analysing iOS logs. It was pretty exciting as an Apple user!



### 1. A few too many

> &#x20;How many different email accounts did the user have?

This took a bit of time to find out, since I had to go through the different users and app login data.&#x20;

The first email: blueisth3best@icloud.com found under the account data tab.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

The second and third email was also easy to find; under the Chrome Login Data tab.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

I then looked through the other app details, and I found the last and final email under the Slack User Data report tab.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

I looked through the other data, and I couldn't find any more emails. So I guess&#x20;

Flag: 4



### 2. autoFill me in on the deets

> Which email, other than their own, was autofilled in Chrome?

Looking throuhg the Chrome Autofill, I could see the emails found for the previous question, and an additional email.

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

Flag: tlouis@kurvalis.com



### 3. 1 fish 2 fish, red fish blue fish

> According to the user’s email accounts, what is his favorite color?

This was the first iOS challenge I found the flag for, and the user's email account could simply be found under the Account Data report tab.&#x20;

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Flag: blue



### 4. Chef Boyardee 2.0

> At which market was the user viewing Chef Pasquale tomato sauce?



### 5. Staying stylish!

> What color shirt did the user chose to put their snapchat bitmoji in?





### 6. Picking up Steam

> What server was the user interested in making?

I did see something related to servers along the way as I was going through the different data in iLEAPP, and it was in the Chrome Keyword Search Terms tab.&#x20;

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

There are two servers being addressed here - CSGO and Rust. I'm guessing however, that with the keyword "Steam", CSGO was the server the user was trying to make, which was right.

Flag: CSGO



### 7. Overlooking Excellence

> What Sports stadium was the user overlooking at Camilien-Houde belvedere?



### 8. Out of this world

> Which terms and conditions site on Tik Tok is named after a space formation?





### 9. You’re going to crush this one!&#x20;

> What light-hearted game did the user spend the most time on?



### 10. Which way?

> Which cardinal direction was the user turning when heading towards RHEINFAHRE?



### 11. First class seats out of here!

> What 4-star Airline flies the most passengers out of the same terminal our user flew out of in Germany?



### 12. Boosting into a new era

> The user was trying to learn German through an application, what promotion featuring a rocket was most commonly shown to the user?





### 13. Q-uestion

> What Chinese networking website was associated with Linkedin?



### 14. You are here

> Which airline lounge was viewed?





### 15. A river runs through it

> At which location did the user travel the most meters according to Apple? (City, Country)



### 16. Lo siento, its going to be a cold one

> What weather front was warned to the user by youtube?

