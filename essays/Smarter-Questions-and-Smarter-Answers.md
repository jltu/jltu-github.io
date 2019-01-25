---
layout: essay
type: essay
title: Smart Questions, Smarter Answers
# All dates must be YYYY-MM-DD format!
date: 2019-01-24
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img class="ui medium left floated image" src="../images/questions.jpg">

## The Importance of Smart Questions 

Progamming is never a secluded practice as there are always links to the open source communities and forums, especially when we are bewildered by a problem. Whether we know it or not, a lot of the problems that we encounter in programming and also in our everyday life have also been enocountered by someone else before. Fortunately, we live in an era of technology where information is just a click away, so more often than not the answers to a lot of our questions can be found online. Despite how accessible information is, the journey to obtain the right information is the challenge, and this points to how well we can phrase our questions. There are a plethora of different solutions and methods of implementation especially in the field of software engineering, where the wide variety of different answers may actually leave you more puzzled than before. By asking smart questions, we can easily obtain the information we need by ensuring our questions are concise yet meaningful. As software engineers, communication is one of the most essential skills to develop, and by asking smart questions, we can obtain smarter answers. 

## Whats a Dumb Question? 

Stack Overflow, also known as the saving grace for programmers world wide, is a question and answer site where anyone can post up a question, and the community can answer it. It is a great resource to resolves issues with code or may want to learn something new. On it, there are a plethora of good questions, bad questions and everything in between. 

In the following example, we examine the components of a bad question. 

---
What is the best way to test a multiplayer network game in unity without build the app ? It is something like in editor unity there is two editor which one is a copied editor. So we can login in one editor and login in second editor with different user. Is there a tool like this ? 

Thanks

---
This is an example of an extremely poor question, where the reader has no clue what the person is even trying to ask. Within the first sentence, the reader is thrown off with vague details and unorderly wording that the reader can't offer assistance even if they wanted to. By the second sentence, the sentence begins to become incoherent, and as the reader is reading this sentence, they would have probably closed the page already as it is too much of a hassle to decipher the question. This goes to show, the importance of asking smart questions. By making sure that the question is concise, coherent and meaningful, the reader will have a better chance of helping or rather even be much more inclined to help. The question should have meaningful headers, concise and informative wording, and should describe the problem's symptoms, problematic steps, and goals. 

## Smarter Questions

---
Thread Title: Does Java JIT cheat when running JDK code?

I was benchmarking some code, and I could not get it to run as fast as with java.math.BigInteger, even when using the exact same algorithm. So I copied java.math.BigInteger source into my own package and tried this:
```
//import java.math.BigInteger;

public class MultiplyTest {
    public static void main(String[] args) {
        Random r = new Random(1);
        long tm = 0, count = 0,result=0;
        for (int i = 0; i < 400000; i++) {
            int s1 = 400, s2 = 400;
            BigInteger a = new BigInteger(s1 * 8, r), b = new BigInteger(s2 * 8, r);
            long tm1 = System.nanoTime();
            BigInteger c = a.multiply(b);
            if (i > 100000) {
                tm += System.nanoTime() - tm1;
                count++;
            }
            result+=c.bitLength();
        }
        System.out.println((tm / count) + "nsec/mul");
        System.out.println(result); 
    }
} 
```
When I run this (jdk 1.8.0_144-b01 on MacOS) it outputs: 
```
12089nsec/mul
2559044166
```
When I run it with the import line uncommented: 
```
4098nsec/mul
2559044166
```
It's almost three times as fast when using the JDK version of BigInteger versus my version, even if it's using the exact same code. I've examined the bytecode with javap, and compared compiler output when running with options: 
```
-Xbatch -XX:-TieredCompilation -XX:+PrintCompilation -XX:+UnlockDiagnosticVMOptions 
-XX:+PrintInlining -XX:CICompilerCount=1
```
and both versions seem to generate the same code. So is hotspot using some precomputed optimisations that I can't use in my code? I always understood that they don't. What explains this difference?

---
The title thread is concise and gets straight to the point. The explanation of the question provides a good background of what the asker was doing when he encountered the problem and the solutions he attempted. The code blocks were also included to provide greater detail of what the asker currently has. This is a sign of a quality question especially when given to the right forum. The question was posted on Stack Overflow, and the question is unique and has not been asked before. The asker provides a really good outline of his problem which makes it easy to reader for potential responders.

The conciseness and informative question that he provided was responded with a quality answer shortly after being posted.

---
Yes, HotSpot JVM is kind of "cheating", because it has a special version of some BigInteger methods that you won't find in Java code. These methods are called JVM intrinsics.

In particular, BigInteger.multiplyToLen is instrinsic method in HotSpot. There is a special hand-coded assembly implementation in JVM source base, but only for x86-64 architecture.
You may disable this instrinsic with -XX:-UseMultiplyToLenIntrinsic option to force JVM to use pure Java implementation. In this case the performance will be similar to the performance of your copied code.
P.S. Here is a list of other HotSpot intrinsic methods.
---

## Conclusion

As software engineers, asking smart questions is essential to learn and obtain new knowledge. Programming is a life long journey and there is so much to learn so that makes it especially important and crucial for hackers to emphasize on smart questions to get smarter answers. 
