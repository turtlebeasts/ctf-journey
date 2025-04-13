# My CTF Journey: From Confusion to Cracked Flags

_By Mriganka Das_

---

## 🎬 How It All Started

It all began with a YouTube search: **"Hacking challenges"**. Among the results, one video title jumped out at me — _"I Played Beginner-Level Security CTFs For 30 Days - Here's What I Learned"_ by Grant Collins. That single video became my turning point. It gave me direction when I felt bored and lost after a year.

---

## 🧠 What Are CTFs?

Capture The Flag (CTF) challenges are puzzle-like problems designed to teach cybersecurity concepts. They range across different genres:

- Web
- Forensics
- Cryptography
- Binary Exploitation
- Reverse Engineering (my favorite!)
- Pwn

---

## 🚀 First Stop: picoCTF

Inspired, I created an account on [picoCTF](https://picoctf.org/). The interface was clean and easy to navigate. I filtered for **Reverse Engineering**, found 64 challenges, and dove in.

### Challenge 1: _Transformation_

A file named `enc` with no extension was attached. Running `file enc` on Linux told me it was a text file. Inside, I saw weird Chinese-like characters. Below the challenge description was this Python snippet:

```python
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```

I broke it down line by line, trying to understand bitwise shifts and character encodings. Despite all efforts, I hit a wall. I felt frustrated — even considered giving up and learning drawing instead. But nope — this ain’t a Disney movie, and I’m not quitting.

So I _cheated_, kind of. I Googled for a write-up. Turned out even the writer I found had copied it from someone else. 😅 Eventually, I understood the trick: the code was an **encoder**, not a decoder — my job was to reverse it. Lesson learned.

> "Everything that looks familiar isn’t always the same." 🔁

---

### Challenge 2: _Keygenme-py_

I downloaded `keygenme-trial.py`. It was a calculator app with a locked feature that required a key. After reading the source, I figured out how the check_key() function worked:

- The first half of the key was static
- The second half was a SHA256 hash

I used print statements to manually debug and rebuild the key. Finally got the flag:

```text
picoCTF{1n_7h3_|<3y_of_01582419}
```

---

## 🖥️ Linux Life: Manjaro KDE Edition

I switched from Linux Mint to **Manjaro KDE** for its customization and style. After two hours of tweaks, my setup felt like a hacker’s workstation. 😎 Still, I missed Microsoft Office (cracked version, of course), so I used Google Docs.

---

## 🎮 Trying New Categories

After a bunch of RE challenges, I checked out other genres.

### General Skills Challenge: _File Copy-Paste_

Yup. Literally copy-pasting a flag from a file. Humbling.

### Python Wrangling:

A Python script with password and flag files. After decrypting it using the script and password, I got:

```text
picoCTF{4p0110_1n_7h3_h0us3_68f88f93}
```

### Netcat Challenge: _Nice netcat_

```bash
nc mercury.picoctf.net 49039
```

The response was a series of ASCII numbers. Wrote a Python script to convert it into characters:

```text
picoCTF{g00d_k1tty!_n1c3_k1tty!_3d84edc8}
```

---

## 🔬 Reverse Engineering Again: _Static ain’t always noise_

Two files: a binary and a script to extract its `.text` section. I:

1. Made the binary executable
2. Ran the script
3. Used grep to search for 'pico' in the strings

```bash
cat static.ltdis.strings.txt | grep pico
```

Flag found:

```text
picoCTF{d15a5m_t34s3r_ae0b3ef2}
```

---

## 📡 Exploring WiFi & MITM

Living in a PG, I became curious about what I could do as a WiFi user. I learned about **Ettercap**, **ARP poisoning**, and **Man-in-the-Middle (MITM)** attacks. This opened up a whole new field to explore.

> "Between source and destination, where do our packets really go?"

---

## 💡 Final Thoughts

This journey wasn’t smooth. I faced confusion, frustration, and even considered quitting. But each flag I captured gave me more clarity and confidence.

CTFs helped me:

- Think like a hacker
- Practice real tools and techniques
- Discover a passion for RE and networking

And this is just the beginning.

---

**Stay curious. Break stuff. Learn more.**

~ Mriganka Das

[GitHub](https://github.com/turtlebeasts)
