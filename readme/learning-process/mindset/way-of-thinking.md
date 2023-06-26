---
description: https://academy.hackthebox.com/module/9/section/45
---

# Way of Thinking

The field of information security is massive. It would be impossible for any one person to learn everything. Let us take the following example:

信息安全领域是十分旷阔的，所以对于任何人来说，想要学完一切知识是不可能的。举个例子：

Imagine you want to become a programmer, and you know that there are more than 200 different programming languages that can be used to create applications that can be cracked by debugging or reverse engineering. If we learned every programming language within 100 hours, we would spend 20,000 hours or 2,500 days (8 hours per day) or, in other words, almost seven years to learn all of these programming languages. As a result, we spent seven years learning all these languages and never tried to debug or reverse engineer the program we created. Great! Let us spend another seven years learning to debug and reverse engineering.

假设你想要成为一个程序员，并且你知道存在超过 200 种编程语言。这些编程语言都可以用来创建可被破解的应用程序，可通过调试或逆向工程来实现这一点。若我们花费 100 小时学习一门编程语言，那么我们需要花费 20,000 小时即 2,500 天（每天 8 小时），换句话说，也就是大约 7 年的时间才能学完所有的编程语言。因此，我们花费了整整 7 年的时间来学完所有的编程语言。不过我们还没有学习如何调试或逆向工程所创建的程序。很好，那就让我们再花费 7年的时间学习调试和逆向工程。

We have got the idea. No one wants to spend so much time on just one area. Furthermore, this is not necessary. We will need some time to learn different technical principles, structures, and processes, but we will not need to spend seven years. Every programming language has its own strengths and weaknesses. Also, if we can obtain a deep understanding of a single programming language, we will learn others much faster. We do not need to learn every programming language to understand how to read their code. All of them follow the same principles which R. D. Tennent initially defined:

从以上描述我们可以明白，在正常情况下，没有人想要单独且也没有必要在一个领域花费如此多的时间。我们确实需要一些时间来学习不同的技术原则、结构以及过程，但我们不需要花费 7 年的时间来学习这些知识。每个编程语言都有其自身的优缺点，若我们能够对某个编程语言有较深的理解，那么我们学习其他编程语言时也会快很多。我们没有必要学习每一个编程语言来理解如何阅读用这些编程语言书写的代码。所有编程语言都遵循由 R.D Tennet 所定义的原则：

1. The Principle of Abstraction（抽象性原则）
2. The Principle of Correspondence（同一性原则）
3. The Principle of Data Type Completeness（数据类型完整性原则）

In information security, we have to learn and understand these principles, structures, and processes quickly. Additionally, we have to adapt our knowledge to the various environments we encounter. We will have many situations where we will not understand how "it" works. That is good. At this point, we have to find out what we do not know. More about that later.

在信息安全中，我们必须快速地学习并理解这些原则、结构以及过程。此外，根据我们遇见的情况不同，我们应灵活运用所学到的知识。在很多时候，我们会遇见不知晓应用程序背后的工作原理的情况。这很好，此时我们必须要找出我们不懂的是什么，这一点稍后会详细介绍。

There are many learning-focused information security communities available to us. Many of these communities provide free reviews of tested applications, vulnerable machines, and guides to help each other and improve their members' skills. When we speak with the other members, we will notice there are generally two types of people.

存在许多以学习为中心的信息安全社区，这些社区提供了如何测试应用程序、存在漏洞的机器的综述，以及如何互相帮助并提高社区成员的技能。当我们与社区成员沟通时，我们会注意到通常有两类人：

* Those that do not know anything.（什么也不知道的人）
* Those who think they do not know anything.（认为自己什么也不知道的人）

This can be very frustrating, and this is a normal part of the learning process. Communication within these communities should be respectful, always keeping in mind that we all started with zero knowledge of this field. This is a critical point of success for the community and everyone learning and working in this field. Within Hack The Box, we can use the Forum and Discord server to interact with the community.

你可能感到有些疑惑，但这是正常的学习过程的一部分。当我们与社区成员沟通时，应对他人保持尊重。要记住，我们都是从零开始的。这也是社区以及每个在该领域学习和工作并取得成功的关键点。在 Hack The Box 内，我们可以利用 Forum 和 Discord 服务器与社区进行交互：

* Forum: [https://forum.hackthebox.eu](https://forum.hackthebox.eu/)
* Discord: [https://discord.gg/hackthebox](https://discord.gg/hackthebox)

Another important point is our knowledge level. Many people do not know their actual skill and knowledge level. This is a complicated topic because penetration testers must have a deep understanding of a wide variety of technologies. As previously mentioned, the problem in this field is the sheer volume of information available to us. We can learn about every topic and still not master any one area, or we can learn about just one topic and become an expert in it.

另一个重要的点是我们的知识水平。许多人不知道它们实际的技能和知识水平，这是一个复杂的主题，因为渗透测试者必须对各种技术都有一个较深的理解。如前所述，信息安全领域的问题就是我们需要学习的知识太多了，不过我们可以学习每个主题的基础但并不掌握任何一个领域，或者我们也可以单独学习某个主题并成为该主题的专家。

Another option is developing our research methodology, the learning process, and how to use this to improve our knowledge. We will be successful if we know how to search for the required information on the internet, and we know how to learn fast and adapt it to the environment we are working in. However, before we can do this, we have to learn and practice how to do it.

另一个选择是培养我们的研究方法、学习过程以及如何利用这些东西来提升我们的知识水平。若我们知道如何在互联网上搜索所需的信息，那么我们就可以知道如何快速地学习并适应我们的工作环境。然而，在我们这样做之前，我们必须学习并实操如何做。

We will become a good penetration tester only through considerable practice. There is no other way to improve our practical skills. For example, we can read 50 books about programming, and we will understand how to read the code. This is the process of passive learning. This can be useful. However, if we need to write our own program, we have to practice active learning, which means we have to write code and test it on our own.

只有经过了大量的练习，才可以成为一个好的渗透测试者，除此之外，没有别的方法可以提升自身的实操技能。举个例子，人们可以阅读 50 本有关编程的书籍来理解如何阅读代码，然而这是被动的学习过程。尽管该过程是有效的，但是，如果需要亲自编写程序，那么就必须养成主动学习的习惯，这意味着必须自己编写代码并调试它们。

One of the most common questions is:

最常见的一个问题是：

When is a penetration tester good enough?

何时才可以说一名渗透测试者是合格的？

We know that one person cannot know everything. In this case, we have to learn how to `find`, `choose`, and `adapt` the information we need.

一个人无法知晓所有知识，在这种情况下，必须学习如何寻找、选择以及调整所需的信息。

Right now, we are considering these three key terms. There is one key term missing.

现在思考一下上述的三个关键术语，并找出一个遗漏了的关键术语。

Which key term is missing from the above list?

上述列表遗漏了哪个关键术语呢？

The crucial missing term is: **`LEARN`**

答案是”**学习**“。

The process of "learning how to `learn`" is not easy. Most people have never truly learned how to learn effectively. For example, in school, our teachers discussed some topics with our class. First, teachers show us just one way to solve a problem. They explained one way to solve the problem, and after that, they gave us exercises to practice further.

学习如何“学习”的过程并不容易。大部分人从未真正学习过如何高效地学习。举个例子，在学校里，老师会在班级上和学生们讨论一些话题。首先，老师会向学生演示求解问题的一个方法，他们会详细地阐述该方法，然后布置一些作业以便学生进一步地练习。

Let us take a closer look at the problem. Look at this simple math equation and try to solve it:

比如说，现在要求解以下的简单等式：

20 \* \_\_\_\_\_\_\_\_+ \_\_\_\_\_\_\_\_ = 65535

This equation is easy to solve, but did we think about how many different ways are there to solve it?

该等式很容易求解，但是请问一共有多少种求解该等式的方法呢？

**Optional Exercise:**

Ask yourself why you didn't solve the problem in a different way. Write it down and try to think about the reasons for choosing the method that you chose. Take as much time as you need for it before you continue.

问问你自己，为何不采用另一种方法来求解该问题。思考你为什么选择某种方法来求解该问题，并在纸上写下来。在你继续本模块的学习之前，尽可能花时间思考一下这个问题。
