---
title: "Syllabus"
layout: default
ready: true
---

# Syllabus <a name="syllabus"></a>

This document and linked resources are your **primary source** for understanding course expectations. Read it carefully and contact the instructor if you receive conflicting information from other sources.

## Basic Facts
- **Course Website**: <{{ site.url }}>
- **Instructor**: {{ site.instructor }}
- **Lecture**: {{ site.lecture_times }}, {{ site.lecture_location }}
- **TAs**: {{ site.tas }}
- **ULAs**: {{ site.ulas }}
- **Lab**: 50-minute closed sections, Phelps 3525, {{ site.lab_times }}

Lab attendance is optional but **highly recommended**, as TAs and LAs are available to assist and you must complete at least one mock interview with a TA or LA during these sessions. We may also use some of the office hour time for this. You may not switch sections because the class is full. If you have a conflict contact the instructor at the end of the first lecture. Start lab/programming assignments during sections and use office hours for additional support.

**Contacting Staff**: Use Ed for course-related communication, including private messages to staff or the instructor. For urgent emails, use diba@ucsb.edu with “CS24” in the subject line; expect a possible delay in response.

## Overview
CS24 teaches efficient problem-solving with data structures and algorithms. You’ll explore abstract data types (e.g., stacks, queues, priority queues, sets, maps), their implementations (e.g., vectors, binary trees), and complexity analysis. You’ll also gain C++ proficiency, leveraging the Standard Template Library (STL) to prepare for technical interviews and future courses.

## Prerequisites
CS24 builds on CS16. You should be comfortable with:
- Basic C++ data types (int, double, char, bool, string)
- Control structures (if/else, while, for)
- Function definition and parameter passing (by value, pointer, reference)
- Variable scope and lifetime
- The `const` keyword with parameters
- Arrays, C-strings, structs, and classes in C++
- Binary, decimal, octal, and hex conversions, and their relation to memory
- Recursion basics and when it’s appropriate

Review CS16 materials or consult TAs if needed as soon as possible.

## Course Objectives
- Understand the C++ memory model (stack vs. heap allocation).
- Implement abstract data types (e.g., lists, trees) using object-oriented principles.
- Analyze algorithm and data structure efficiency with Big-O notation.
- Apply data structures to solve complex problems in C++.
- Master STL components for technical coding interviews.

## Resources
All activities except programming assignments and exams are optional. Lectures are recommended, with slides and code on GitHub. Reading is primarily assigned from Main & Savitch. 

- **Textbooks**:
  - *Data Structures and Other Objects Using C++* by Michael Main and Walter Savitch (Reading assigned from this book, also the standard textbook for CS32)
  - [OP] *Open Data Structures C++ Edition * by Pat Morin (free at <https://opendatastructures.org/>)
  - [Dasgupta] *Algorithms* by Dasgupta and Vazirani <https://cseweb.ucsd.edu/~dasgupta/book/toc.pdf>
  - *Problem Solving with C++* by Walter Savitch (CS16 standard textbook)
  - *Data Structures and Algorithm Analysis in C++* by Mark Allen Weiss (CS 130A standard)
- **Visualization**: <https://visualgo.net/>
- **C++ STL Documentation**: <https://en.cppreference.com>
- **Support**: Instructor office hours (see website), TA/LA drop-in hours (Phelps 3525, times on course calendar)

**In-Class Participation**: Join iClicker Cloud at <https://join.iclicker.com/AXZR>. Participation is ungraded but encouraged.

## Discussion Forum: Ed
Use Ed for Q&A (link on Canvas). Post public questions when applicable; for coding issues:
- Share the smallest relevant code snippet (not screenshots/photos).
- Make posts private if including significant code.

## Grading
- **LeetCode + Mock Interview**: 10%
- **Programming Assignments**: 30% (labs + larger projects)
- **Midterm**: 25%
- **Final Exam**: 35%

A **minimum 65% on the final exam** is required to pass, ensuring core concept mastery. Below 65%, your grade is capped at D unless special circumstances apply (contact instructor). Letter grades (A, B, C, D, F) are set at the instructor’s discretion; A+ goes to the top 5% (no other +/- grades).

### LeetCode + Mock Interview(10%)
Complete 10 medium LeetCode problems from the assigned list (on the course website) to build algorithmic skills aligned with course topics and exams.
- **Setup**: Create a LeetCode account (format: `DS_[YourInitials]_[RandomNumber]`, e.g., `DS_JD_1234`).
- **Submission**: By Monday, Week 2, 11:59 PM, submit a Google Form (link on lab01) with your name, ID, and profile link.
- **Task**: Solve 10 problems, with at least one from each of the problem sets provided, by Friday, Week 9, 11:59 PM and complete one mock interview with TAs/LAs by the last office hour on Friday, Week 10.
- **Grading**: Grade for leetcode (5%) = (Accepted solutions / 10) * 10%, with at least 10 attempts (by the end of week 9) and completion of mock interview required for credit (e.g., 8/10 = 8%; < 10 attempted OR mock interview not completed = 0%).
Grade for mock interview = 5%
- **Monitoring**: Progress may be checked (e.g., Week 5), but only the final count matters.

Schedule your mock interview early (signup form will be made available by week 2)

## Late Policy
You have **five late days** total, with a **maximum of three days** per assignment, no penalty within this limit. Beyond this, a 10% deduction applies per day (up to one week), after which no credit is given unless approved for extenuating circumstances.

## Pair Programming
Some assignments allow optional pair programming (2–3 students coding together at one terminal, like a lab partnership). Benefits include:
- Industry relevance and employer value
- Improved collaboration skills (feedback from UCSB CS employers)
- Enhanced learning and grades (research-backed, positive student feedback)
- Watch: <http://bit.ly/pair-programming-video> (10 min)

## Use of AI Tools
AI tools (e.g., ChatGPT, GitHub Copilot, Grok) can support learning but must not replace your effort. Usage rules:
- **Permitted Use**: Allowed only for assignments labeled “AI-permitted” in instructions; prohibited elsewhere (e.g., exams, unmarked tasks).
- **Constructive Engagement**: Use AI to:
  - Clarify concepts (e.g., “Explain binary search trees”)
  - Get code feedback (e.g., “Improve my queue implementation”)
  - Explore design trade-offs (e.g., “Hash table vs. array pros/cons”)
- **Prohibited Use**: Generating full solutions, large code segments, or completing assignments (e.g., “Write a BST in C++”) is academic dishonesty, even when permitted. Debugging help is okay; rewriting your work is not.
- **Documentation**: Submit a log (e.g., text file or screenshots) of AI interactions for permitted assignments, showing constructive use and your own work. Earn up to a 5% assignment bonus on assignments where AI tools are permitted for thoughtful engagement (instructor’s discretion).
- **Tool Choice**: Any AI tool is allowed; identify it in your log.
- **Consequences**: Unauthorized use, missing logs, or misuse equals academic dishonesty (see below).

## Academic Integrity
Check each assignment’s collaboration policy—some are individual, others allow pair programming. Review UCSB’s Academic Integrity guidelines: <http://studentconduct.sa.ucsb.edu/academic-integrity>. Violations (e.g., cheating, plagiarism, unauthorized AI use) result in:
- **First Offense**: Zero on assignment + one-letter grade drop
- **Second Offense**: Course failure
- All cases reported to the Office of Student Conduct

Key rules:
- No unauthorized materials, study aids, or services (see AI policy).
- Cite all sources, including web searches, in assignments.
- Keep graded work private (no public posting; Git repos must be private).
- Don’t share solutions outside your pair/group.
- No exam info from prior takers or non-approved sources (e.g., Chegg).
- Pair programming requires joint coding, not split work; submit one version on Gradescope with partner names.

## Exam Makeups
Makeups are granted only for unavoidable emergencies (e.g., major illness), not scheduling conflicts. Check exam dates early!

## Disabled Students Program (DSP)
UCSB accommodates students with disabilities via DSP (2120 Student Resource Building). Register early with documentation; accommodations are honored only through DSP. More info: <http://dsp.sa.ucsb.edu>.

## Disclaimer
Policies are accurate but may change at the instructor’s discretion within UC guidelines.

[Back to Syllabus](#syllabus){: data-ajax="false"}


