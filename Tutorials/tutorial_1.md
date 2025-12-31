---
layout: page
title: Tutorial 1 - Java, UML, OOPs
permalink: /tutorials/tutorial-1
parent: Tutorials
nav_order: 1
---

## Tutorial 1 - Introducing Java through the lens of UML and OOP

---

### Slides

Can be found [here](https://docs.google.com/presentation/d/1LVBA0DLn97_cRAWNm8Xp9fISGsf0QiUPL89aWp6WRIg/edit?usp=sharing).

### Resources

1. An Introduction to Abstraction ([link](https://www.lesswrong.com/posts/CHSBRLWY5bzZdchFF/a-thorough-introduction-to-abstraction))
2. Documentation on OOPs in Java ([link](https://docs.oracle.com/javase/tutorial/java/concepts/))
3. JVM, JDK, JRE ([link](https://www.ibm.com/think/topics/jvm-vs-jre-vs-jdk))
4. Some more on the `main` function ([link](https://www.baeldung.com/java-main-method))

### Aside

1. A paper on UML->Java ([link](https://dl.acm.org/doi/abs/10.1145/353171.353184))
2. On the evolving nature of Java Interfaces ([link](https://blogs.oracle.com/javamagazine/post/the-evolving-nature-of-java-interfaces))

---

### Questions from the Tutorial

**1. How many `main` function can exist within an app?**

There can only be one main method that serves as the entry point for program execution which must be defined using:

```java
public static void main(String[] args)
```

- If a Java file contains multiple classes, each class can have its own main method, but only one of them can be executed as the program's starting point.
- If there are multiple main methods with the correct signature in the same class (as in multiple having `String[] args`), it will result in a compilation error.
- However, Java allows for method overloading, meaning you can define multiple methods named `main` in the same class or different classes, provided they have different parameter lists soft of like:

```java
public static void main(int i)
public static void main(String s)
```

These overloaded methods can exist alongside the standard main method, but only the original `public static void main(String[] args)` will be recognized by the JVM as the entry point.

