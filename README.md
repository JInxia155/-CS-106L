Download Link : https://programming.engineering/product/putting-1-on-your-resume-by-completing-a-stl-compliant-hashmap/

# CS-106L
Putting #1 on your resume by completing a STL-compliant HashMap
In this assignment, we will be putting #1 on your resume by completing a STL-compliant HashMap.

Recall that the Map abstract data type stores key value pairs, and provides effcient lookup of the value of any key. There are two versions of this in the STL:→std::map, traditionally implemented using a balanced binary search tree, and std::unordered_map (introduced in C++11), which uses a clever technique called hashing and supports the most map operations in constant time (!).

In this assignment, you will be given a nearly complete implementation of a HashMap (the name of this data structure in the Stanford C++ library). The starter code is nearly complete, but is not “STL-compliant”; for example, copy and move semantics are not supported yet. Your goal is to extend it so it becomes an STL-compliant, industrial strength, robust, and blazingly fast data structure.

A hashmap is a bit of a complicated data structure, but we’ve given you nearly all of the implementation of it.

In brief, this is how it works:

A hashmap stores an array (represented by the private vector _buckets_array in our HashMap) of

“buckets”.

Each “bucket” is a linked list: linked lists are made up of nodes, which are defned in hashmap.h.

Each node in these linked lists contains one key-value pair that is contained in our map. In the node

struct, this is the feld value, of type value_type. value_type is a type-alias for a std::pair<K, M>.

Check out its defnition near the top of the .h fle!

When a user of the hashmap class tries to look up or insert a key, the HashMap class frst converts the key, no matter what type it is, to an integer. It does this using the hash function, stored in the private member varibale _hash_function. For our purposes, this will always be the default hash function in the STL. Then, the HashMap class mods that integer by the number of buckets in _buckets_array. This is the index at which HashMap will insert or look for the key. From here, its just a matter of traversing the linked list stored at that index to fnd the key in question (it is possible that multiple keys are stored in the same index because their hashes, or the mod of their hashes, are the same!)

The HashMap will occasionally increase the number of buckets and re-hash and store everything to make sure each index doesn’t have too many keys stored there. This keeps all operations very fast, because it is very quick to look up an index in an array, and we are guaranteed to have very short linked lists there!

Dont worry if you don’t feel super comfortable with HashMaps! We have implemented all of this logic for you, and we highly encourage you to read through the code to understand what is happening. However, this assignment does not ask you to implement anything except some SMFs, which only deal with initializing the private member variables.

You will not necessarily write a lot of code on this assignment (~20 lines), but some of your time will be spent on understanding the starter code given to you, and reasoning about design choices and common C++ idioms. You may optionally work with a partner. We recommend having a partner to discuss the design questions. If you choose to work with a partner, we ask that you and your partner submit a single version of the assignment among both of you. This means that you will ideally be working with your partner on a shared version of the code and short answer questions. Feel free to start a shared Google Doc, a private GitHub repository, or anything else that you’d need to keep track of a shared version of the code. You may also choose to schedule video chat sessions with each other to work on the assignment.

Download And Set Up Assignment

1. We suggest running the code on the Myth machines to prevent any issues with your computer’s setup. If you haven’t already, set yourself up in VS Code. The instructions for this are on the assignment setup page. We recommend the alternate SSH setup.

2. Download the starter code here: Starter Code

3. In terminal, scp your Assignment 3 starter code to your 106L folder in myth. scp LOCAL_PATH

<yoursunetid>@myth.stanford.edu:MYTH_PATH

LOCAL_PATH is the place on your laptop where you just downloaded the starter code. It will probably

be something like Downloads/HashMap_Starter.zip.

MYTH_PATH is the path on myth where you keep your CS106L folder.

You can fnd this by 1) sshing into Myth using ssh <yoursunetid>@myth.stanford.edu, 2) entering

your password and then 3) cding to your CS106L directory and fnally 4) printing out the path to this

folder using pwd.

    Unzip the folder in myth by running unzip HashMap_Starter.zip.

    Now, you should be able to open your Assignment 3 code using whichever VS Code setup instructions you have been using all quarter!

2023/4/9 15:45 CS 106L: Standard C++ Programming

In your move constructor or move assignment operator, why did you have to std::move each member,

even though the parameter (named rhs) is already an r-value reference?

PleaseSubmittingsubmithashmap.h, hashmap.cpp and short_answer.txt to Paperless

web.stanford.edu/class/cs106l/assignment2.html 4/4
