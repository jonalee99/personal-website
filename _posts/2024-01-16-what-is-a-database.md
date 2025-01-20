---
layout: post
title:  "What is a database?"
date:   2025-01-12 10:59:45 -0500
categories: cloud 
---
Way back when, the internet did not exist, files were stored in cabinets. To find a document, you would open the drawer and see the carefully handwritten labels peeking back up at you. Good thing they're alphabetically ordered - it makes the search much faster.

In the age of information, many young adults in their 20s never experienced the challenges of maintaining paper records. They cannot recall wrangling with files in the wrong drawer or handwriting so messy that it cannot be read. Why does anyone need a bookshelf filled with volumes of a dusty encyclopedia when they can easily search Wikipedia? These days, no fact is too small or obscure to find in a Google search with Reddit appended at the end.

All this begs the question, where is all the data on the internet stored? Is there a person sorting through filing cabinets on the other end of the https connection to find us the information we search for? Ding! A new request appears as they scramble to find the correct file - "Why is the sky blue during the day, but black at night?" This situation is unlikely and a bit silly to imagine, but it's worth considering given how little the average person understands how data is stored and retrieved.

Introducing the database - a program that stores data. This behemoth of a concept puzzles grandparents and new-grad tech hires alike, so let's break it down.

## What is data?

Information is order made from the chaos. It's the difference between static noise and your favorite pop song on the radio. Anybody or anything can make static noise, like a waterfall, but who can croon your favorite ballad other than Celine Dion? Well, Celine Dion or a recording of her. So how do we preserve and transmit information? Cavemen scratched pictures onto walls that their children could view. Professors write, publish, and sell books to their ensnared students. Radio hosts turn their voice into radio waves that can be heard by anyone in range with a radio. There are many options to encode information onto many different mediums.

There is no medium more important these days than digital. Digital data is data represented by digits. Pop quiz, how many digits do humans have? Ten fingers and ten toes. Naturally, it follows that humans count in clusters of ten. If there are twenty bananas, that's two groups of ten bananas - 2 groups of 10 bananas - 20 bananas. This method of counting is called decimal. Great job humans! No banana will go uncounted. However, humans do not power the data centers that store digital data, computers do.

In contrast, computers store digital data in binary digits, 0s and 1s. While twenty-five bananas are represented to humans as 25 bananas, machines represent it as 11001 bananas. There are many [great explanations](https://www.youtube.com/watch?v=sXxwr66Y79Y) on how to convert between the two, but if you are unfamiliar, try figuring it out with the table below. Remember that computers only have 2 digits to work with instead of 10.

| Decimal | Binary |
|---------|--------|
| 1       | 1      |
| 2       | 10     |
| 3       | 11     |
| 4       | 100    |
| 5       | 101    |
| 6       | 110    |
| 7       | 111    |
| 8       | 1000   |
| 9       | 1001   |
| 10      | 1010   |

A natural follow-up question is why do computers need to use binary instead of decimal? The answer lies in the physical state underlying the information. It is easier to differentiate between two states than ten states. You can look across the room and easily tell if a light switch is flipped up or down because there is such a difference in the physical state. Compare this to guessing what setting a sliding light switch is set to 3/10 brightness or 4/10 brightness. With ten states to choose between, the likelihood of choosing incorrectly vastly increases. What follows is that fewer states to represent results in less ambiguity.

Computers take advantage of the lack of ambiguity in two states to seamlessly store and transmit data. For example, persistent data can be stored by computers on discs. The number ten, represented in binary as 1010, can be represented by the disc's magnetic polarization (+, -, +, -). A computer can read that disc and transfer the number into the processor, represented by electricity either flowing through a transistor or not (on, off, on, off). Then the computer can send this number over a wire by setting a series of voltages that another computer is listening to (+, -, +, -). The chain goes on forever. Each medium of digital information chooses to represent data in binary because it is the easiest way to do so.

But how do computers turn a stream of boring numbers into interesting things like TikTok videos, Spotify music, Xbox games, Reddit posts, and Uber pickups? Imagine how useless your GPS would be if it gave you your route as `1000101001010101101010`. A much more useful representation of the data would be in an interactable map guiding you to your destination. Understanding this transformation is not only fun but also key to understanding how databases are used.

Let's start with text. 1, 2, 3 -> a, b, c. That's easy. So how many numbers do we need to store text? The alphabet has 26 letters. Each letter can be uppercase and lowercase, so that means 52. There exists a variety of punctuation and symbols - `,`, `.`, `'`, `"`, `:`, etc... In total, 39. That sums to 95. There are a few more characters computers must understand, like new lines. In total, the full English alphabet and its metadata can be mapped to 128 numbers. The most common mapping used is called the [American Standard Code for Information Interchange](https://www.ascii-code.com/) (ASCII). "Hello World!" can be [transformed](https://www.browserling.com/tools/text-to-ascii) into `72 101 108 108 111 32 87 111 114 108 100 33`. Try it yourself!

Just like text, video and audio can be mapped onto a series of numbers. However, it is not as straightforward as text due to the complexity of the information. Therefore, there are a variety of supported encoding-decoding protocols for video (HEVC, VP9, H.264) and audio (MP3, AAC, FLAC). Different protocols offer different pros and cons, usually trading off quality and processing speed for data size. I won't go into more depth due to their complexity, but the principle remains the same - representing data in a digital format by turning data into numbers. Now how are all these numbers stored?

## File Systems

Every computer has a file system. A file is a container for the digital data, a sequence of numbers. On a Windows computer, users can interact with it by opening the File Explorer application. On a Mac computer, users can use Finder. Users can create, open, delete, and move files and folders. It seems that everything we need to interact with data is already present.

For example, a program that needs to store user data could create a new file in a users directory for every new user. The directory looks like:

```
Users
 ├── Jonathan
 |── Jeff
 └── Ruby
```

Each file contains the user's phone number and address in a text file:

```
File: Users/Jonathan

Address: 123 Easy street
Phone Number: 123-456-7890
```

Given the program is running on the same computer, there seems to be no issue with this setup. However, what happens when we add too much data per user? On Linux, the maximum file size is around 16TB. In that case, we'd need to split some users into two files.

```
Users
 ├── Jonathan_1 (16TB)
 ├── Jonathan_2 (4TB)
 |── Jeff
 └── Ruby
```

This creates a host of new issues. How is the data split? Which file contains Jonathan's phone number? This is a simple example of an issue that comes up when using file systems, but there are many more. Some other issues include concurrent access, access control, replication, efficient search and scanning, enforcing data structure... All issues a developer writing a simple program do not want to deal with.

This is not the file system's fault. A file system is built to allow the operating system interact with the hardware. The file system imposes just enough limitations to protect the computer itself, but not the application running on the computer. If only there was a way to hide the sharp edges of the file system to make it easier for the software developer...

## Databases

Introducing the database. In the simplest terms, a database is a program that helps manage data. This can be in the form of enforcing data structure, preventing data corruption, making backups, encrypting data, or offering easy ways to search for data. It works as an intermediary between the file system and the program.

```
Hard drive <-> File System <-> Database <-> Program <-> You!
```

For example, when you create an account on Instagram, your iPhone sends your username/password to an Instagram server sitting in a data center. This server then sends your username/password to a database. The database saves the data on a hard drive using the file system of the computer it is running on. The database replies to the Instagram server that the data was saved, then the Instagram server replies to your iPhone that your account was succesfully created.

```
iPhone -> Instagram server -> Database -> Hard drive
```

Now, when you login, your phone send your username/password to the Instagram server. The server asks the question, "Can I see the password for this specific username?" The database efficiently fetches the given password and returns it to the Instagram server. The Instagram server compares the password in the database with the password received from your iPhone. If they match, it logs you on.

There is a broad offering of different databases which offer different features. There are three broad axis used to categorize databases:

1. How is the data structured?
2. How much computation does it take to store and query data?
3. Can this database be spread across multiple computers?

In general, the more structured the data is the more computationally intensive data insertion and retrieval is. The 3rd property, if the database can be used across distributed computers, is more independent, but tends to increase computational load as well.

From paper records to file systems to databases, the evolution of data storage reflects humanity's quest for efficiency and accessibility. Databases bridge the gap between raw digital data and meaningful applications, making them indispensable in today's data-driven world. Whether you're logging into Instagram or asking your GPS for directions, databases are working behind the scenes to deliver information seamlessly. Stay tuned as we dive deeper into how to choose the right database for your needs!
