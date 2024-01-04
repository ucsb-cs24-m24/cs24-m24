---
title: "Syllabus"
layout: default
ready: true
---

# Syllabus <a name="syllabus"></a>

This document and others linked within it should be your PRIMARY source for understanding the expectations of this course. Be sure to read it *carefully*.
You must contact the instructor for clarification if you receive information from any another source that is in contradiction to what is provided below.

## Basic Facts
* **Course Web Site**: <{{ site.url}}>
* **Instructor**:  {{site.instructor}}, office hours Mondays 2p -3p, HFH 1155
* **Lecture**: {{ site.lecture_times}}, {{ site.lecture_location}} 
* **TAs**: {{ site.tas}}
* **ULAs**: {{site.ulas}}
* **Lab** (50 minute closed lab sections), Phelps 3525, {{ site.lab_times}}  

If you have a section conflict you may informally switch your section time with another student and consistently attend the new time. If you are working with a pair partner, you may attend any section that works for both of you. No need to email the instructor. Section attendance is highly recommended because that's the time when LAs and TAs are available to help you. There is an expectation that you start working on each lab/programmming assignment during sections and use office hours as extra help. 

Contacting the course staff, including the instructor: Please use the class discussion forum, Piazza rather than email for course related communication. You can send private messages on Piazza to either the entire course staff or directly to me. If you must email me using my email address (diba@ucsb.edu), please put `CS24` in the subject line, and know that there may be a delay in the response.

## Overview

The goal of this class is to solve problems efficiently using data structures and algorithms. You'll learn about abstract data types e.g. stacks, queues, priority_queues,  sets,  and maps;  the concrete data structures used to implement them, e.g. vectors, and binary trees; and how to reason about the complexity of the operations performed on the data structures. Another goal is to become proficient with coding in C++ and using the C++ Standard Template Library (STL) well enough to succeed in technical coding interviews and future classes! 

## Resources

Everything in this class is optional except the programming assignments and exams. Lecture attendance is not required but highly recommended. Lecture slides and code will be available on GitHub. There is no required textbook.  Everything we talk about in this class is common
computer science  material,  and you can find it  online in  whatever format you
like best.  Below are recommended textbooks:

- **Data Structures and Other Objects Using C++** by Michael Main and Walter Savitch\
  This used to be the standard textbook for other CS 24 courses.
- **Problem Solving with C++** by Walter Savitch\
  This is an optional textbook for other CS 24 courses.  It's also the
  standard textbook for CS 32.
- **Data Structures and Algorithm Analysis in C++** by Mark Allen Weiss\
  This is the standard textbook for CS 130A.

A great way to learn data structures is to visualize them. I recommend using <https://visualgo.net/>.

**In class participation using iclicker cloud** 
Join the class use this link to engage with the course content: <https://join.iclicker.com/GLRN>
iclicker participation does not count toward your grade.

## Piazza

We'll be using Piazza as a Q&A forum. If you have a question that might apply to
other people as well, it's better to ask on Piazza than to send an email.

If you ask coding questions on Piazza, please:

- Post the smallest section of code that fully describes your problem.
- Include any code as a code snippet, not a screenshot or cell phone photo.
- If you include more than a few lines of your code, make your question private.

Link to join Piazza: <https://piazza.com/ucsb/winter2024/cmpsc24/resources>

## Grading

Your final score will be weighted as follows  
* Programming assignments: 50% 
* Midterm: 15% 
* Final Exam: 35% 

Please check the collaboration policy of each programming assignment - some must be completed individually while others may be completed in pairs using a pair programming style (more details below). 

You have  six late days  to use over the course  of the quarter.  Any individual
assignment  may be turned in  up to three days late.  As long as your
total late time  does not exceed six days  there is no penalty,  but  using more
than six days will drop your final score by 10% per extra day used.

The cut-offs for letter grades will be at the discretion of the instructor, you can expect grades to follow the standard scale.

## About pair programming

Some of the programming work in this course will be done using a style of programming known as &quot;pair programming&quot;. This is where two people (in rare cases, three) work together at the same terminal to solve a programming problem.
It is similar, in some ways, to having a &quot;lab partner&quot; in a Biology, Chemistry or Physics course.
For the assignments where pair programming is mentioned, it is optional. But here's why we recommend it:
* Pair programming is a real-world skill that is highly valued by employers.
* Many companies use pair programming extensively, including several local area employers of UCSB CS graduates.
* Companies that employ UCSB CS and CE grads tell us that our graduates have good technical skills but need better skills and working in pairs and groups to solve problems.
* Incorporating  pair programming into our curriculum is part of our response to this &quot;real-world&quot; feedback.
* Most students find it helpful and enjoyable—UCSB CS students from 2009-2010 that were surveyed about their pair programming experiences overwhelmingly reported positive results.
* There is also evidence in the scientific literature that it improves student learning, and helps you get better grades.
* To learn more about pair programming, watch the following video (it takes less than 10 minutes): [http://bit.ly/pair-programming-video](http://bit.ly/pair-programming-video)

## What you should know to be ready for CS24

Here's the  list of a few important things you'll need to know to be ready for CS24.

* A few of the basic data types of C++, including at least, int, double, char, bool, string
* The basic control structures of C++ (if/else, while, for etc.)
* Defining functions in C++, and passing parameters to functions in three different ways (by value, by pointer, and by reference)
* Scope and lifetime of variables in C++
* The use of "const" with parameters to functions
* Using arrays in C++, and C-strings (null-terminated character arrays)
* Defining and working with structs and classes in C++
* Converting from binary to decimal, octal, and hex, and back again&mdash;and how this relates to how C++ programs store various kinds of data in memory.
* The basic principles of recursion, and some idea of when a recursive solution is appropriate.


# Course objectives

* Learn about the C++ Memory Model and Dynamic Memory allocation 
* Learn about the difference between space allocated on the stack (e.g. local variables) and space allocated on the heap (with the new and delete operators)
* Learn object-based programming techniques: abstraction and encapsulation.
* Learn to specify, implement and apply lists, trees and other data structures using OOP principles.
* Learn to distinguish algorithms and data structures on the basis of efficiency by analyzing their complexity (Big-Oh).
* Learn (and practice) to produce better programs more quickly and with less stress.


## Academic Integrity

Please read about actions that are categorized as Academic Dishonesty on the UC Santa Barbara Office of Student Conduct website:
<http://studentconduct.sa.ucsb.edu/academic-integrity>

Academic integrity violations will be taken seriously, reported to the campus-wide Office of Student Conduct, and will result in either lowering your grade by a whole grade point or an F in the course. Key facts about academic integrity related to CS24:

* Using or attempting to use materials, information, study aids, or commercial “research” services not authorized by the instructor of the course constitutes cheating. 
* You may not use coding aids like Co-pilot and ChatGPT (unless explicitly stated on the assignment)
* Representing the words, ideas, or concepts of another person without appropriate attribution is plagiarism. 
* Whenever another person’s written work is utilized, whether it be a single phrase or longer, quotation marks must be used and sources cited. Paraphrasing another’s work, i.e., borrowing the ideas or concepts and putting them into one’s “own” words, must also be acknowledged. If you refer to any information through a websearch for programming assignments, cite the source in your solution.
* Do not publicly post any component of the graded components in this class (such as book activities, labs, programming assignments, and exams) or solicit answers from sources that are not explicitly allowed for each assignment. These are the intellectual property of the instructor.
* Ensure that the visibility of your git repositories are private.
* Do not share partial or complete solutions for programming assignments or labs with other students in the class who are not in your group. 
* Before and during taking any individual assessment, do not attempt to obtain information about the contents of the exam from students who have already taken it or from any nonauthorized sources (Chegg, stack overflow, or any other paid tutoring service).
* If working with a pair partner on assignments, add the name of your partner to the assignment on Gradescope and only submit one version.
* Follow pair programming guidelines when collaborating on programming assignments. Pair programming on an assignment does not mean that you can simply divide the work for the assignment, rather you are expected to code together following pair programming guidelines. 

Policy on all cheating cases is:
- All cases will be reported to the office of student conduct.
- **First Offense:** Zero on the assignment _and_ final grade lowered by one letter.
- **Second Offense:** Fail the class.


## Makeups for exams

* Makeups on exams will only be given if there is an emergency situation that you could not predict or avoid including but not limited to major illness

* No makeups will be given if you have a conflict with any of the exams for this course. Please check for conflicts with the final!


## Disabled Students Program (DSP)
UCSB provides academic accommodations to students with disabilities. Students with disabilities are responsible for ensuring that the Disabled Students Program (DSP) is aware of their disabilities and for providing DSP with appropriate documentation. DSP is located at 2120 Student Resource Building and serves as the campus liaison regarding issues and regulations related to students with disabilities. The
DSP staff works in an advisory capacity with a variety of campus departments to ensure that equal access is provided to all disabled students.
If you have a disability that requires accommodation in this class, please go see the DSP very early on in the quarter. I will only honor these types of requests for accommodation via the DSP. More information about the DSP is found here: [http://dsp.sa.ucsb.edu](http://dsp.sa.ucsb.edu)


## Disclaimer
The course policies have been provided as accurately as possible, but are subject to change at the instructor's discretion, within the bounds of UC policy.



[Back to Syllabus](#syllabus){: data-ajax="false"}
