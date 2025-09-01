---
layout: post
title: \[Java\] equals() vs ==
date: 2025-09-01 16:00:00 +/-1000
categories: [Learning, Java]
tags: [java]     # TAG names should always be lowercase
author: mayRhee
---

Initially I knew that `.equals()` method is true when the contents of two reference type data are same,
in contrast `==` is only true when the address of the reference type data are same.

However, I found few edge cases that I couldn't adjust my previous knowledges.

## 1. Object's initial .equals() is same as ==

Initially, `Object` type's `.equals()` methods are implemented like this.

```java
    // Object.java

    public boolean equals(Object obj) {
        return (this == obj);
    }
```

And in the reference types which inherits Object(e.g. String, Integer) `.equals` is **overriden** as different implementation.
Like this.

```java
    // String.java

    public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        return (anObject instanceof String aString)
                && (!COMPACT_STRINGS || this.coder == aString.coder)
                && StringLatin1.equals(value, aString.value);
    }
```

```java
    // Integer.java

    public boolean equals(Object obj) {
        if (obj instanceof Integer) {
            return value == ((Integer)obj).intValue();
        }
        return false;
    }
```

## 2. Java String interning

At first I saw below code, I couldn't understand.

```java
    String s1 = "world";
    String s2 = "world";
    System.out.println(s3 == s4); // true
```

I thought that the value will be `false`. 

Since s1 and s2 are different reference type variable, I assumed the address would be different.

However, it was not true. if we print `System.identityHashcode(s1)` and `System.identityHashcode(s2)`, we could see they have same hashcode(address).

How this thing happens? Because [String.intern()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#intern()) methods makes all strings having same contents share same memory. 

As the oracle document, there is the pool of String, and if the intern method invoked and the pool contains the string that is equal to this String method as determined with `.equals()` method,(=So if the contents of the variable are same), the **string from the pool is returned.**

It follows that for any two strings s and t, s.intern() == t.intern() is true if and only if s.equals(t) is true.

So that's why if the contents of String variables are same, their references are also same.

Reference: [Stackoverflow: What is Java String interning?](https://stackoverflow.com/questions/10578984/what-is-java-string-interning)