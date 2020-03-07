---
title: Wiki Style Guide
description: 
published: true
date: 2020-03-07T09:08:09.534Z
tags: documentation, wiki
---

# Wiki Style Guide

## General Guidelines
The following sections provide guidelines for both sentence composition and syntax usage. Follow these guidelines to ensure your document's tone is consistent with that of other OpenMandriva documentation.

### Composition
#### Voice
Instructions and rules use an *active voice*, presenting confidence to the reader without sounding demanding.  An active voice provides clear direction.  It shows the reader what to do and gives expected results.  Active voice leaves the reader with the impression an author stands behind the written work.

#### Avoid Passive Voice Unless Necessary
*Passive voice* is completely correct grammatically, but it is a barrier to reader comprehension. The passive voice flips conventional sentence structure around. It moves the verb and direct object forward to the first half of a sentence, and places the main subject in the second half of a sentence. Often a simple restructuring of the sentence makes it active. Long passive sentences frequently take multiple reads before a reader grasps the full meaning.

`ACTIVE:  Select a strong password to improve personal security.`

`PASSIVE: Personal security improves by a strong password being selected.`

#### Context

Avoid writing out of context.  Adhere carefully to the subject matter of the document, chapter, section, and paragraph.  Use references as appropriate, structuring documents so each new part builds upon the last.  Avoid making the reader skip ahead to put current parts in context. Provide a link to related documentation if the reader may need it for clarification.

#### Emphasis

Emphasis is most effective when used sparingly.  Use methods of emphasis such as boldface, underlining, or oblique text to draw attention to a new term.  Use admonitions to set off notable material. Another acceptable way to emphasize a point is with varying sentence formation or word choice. The best documentation writers plan ahead for emphasis, applying it with careful consistency throughout the document.

#### Accuracy and Precision

Accuracy and precision make or break any document.  This axiom applies equally to technical and literary accuracy.  Choose words after considering as many usage cases as possible.  For example, "go to" is not as precise as "click," yet "click" may not be accurate for all interface interactions.  The term "select" is accurate in any usage case and sufficiently precise.  Don't become too preoccupied in an attempt to cover all potential usage cases.  Covering rare side cases elongates a document beyond reason, and the reader loses focus.

#### Tense

Tense is the time in which language takes place. There are three main tenses: past, present, and future. Select an appropriate tense for the document and adhere to it.  For technical documentation, use the present tense whenever possible.  Maintaining the same tense for each statement in a document is vital for clarity.  Keep the same tense for all sequential tasks in a procedure.

### Usage

#### Contractions

Avoid contractions, the combination of two words with an apostrophe replacing one or more letters.  Contractions reduce the readability of documents and make translation more difficult.  Other cultures and languages interpret contractions differently, and this confusion conflicts with the goals of the OpenMandriva Documentation Project.

#### Pronouns

Pronouns are words language uses to replace specific noun phrases. Good writers must strike a balance between over-repeating a noun phrase, and using pronouns to stand in for nouns. A general rule to preserve clarity is to never repeat noun substitution with a pronoun in two consecutive sentences. Readers of technical documents need constant reminders on the exact subject the author is writing about. Prevalent use of pronouns cause readers to guess the subject a sentence is referencing. These assumptions reduce the effectiveness of documentation.

Avoid most personal pronouns in documentation, including the following:
* Subjective personal pronouns ("I," "he," "she," "it," "we,")
* Objective personal pronouns ("me," "her," "him," "us")
* Possessive personal pronouns ("my," "her," "his," "our")

Also avoid:
* Reflexive pronouns, such as "yourself" or "himself"
* Intensive pronouns, such as "he himself" or "(you) do it yourself"
* Resist overuse of "you", "your", and "one/one's"

Occasionally situations require the second personal pronoun "you," and its attendant forms for clarity.  Maintaining an active voice is paramount over avoiding the second personal pronouns.  "You" and "your" are appropriate words to indicate action or possession on the part of the reader. 

Indefinite pronouns such as "this" or "that" without an antecedent make it tough for a reader to follow an author's meaning. Favor writing an exact noun phrase whenever possible over the vague words "this," "these," "those," and "that."

`INCORRECT: Edit your yum configuration files to use geographically close mirrors.  This allows you to
update your system faster.`

`CORRECT:  Edit the yum configuration files to use geographically close mirrors for faster system updates.`

When eliminating indefinite pronouns, a cumbersome long sentence may result from joining too many clauses.  Use indefinite pronouns to break long sentences up to improve clarity, but always provide a proper antecedent. 

`INCORRECT: Stay current with recommended updates to your operating system in order to improve functionality of 
applications, remove security risks, and automatically resolve performance issues solved from bug reports.`

`CORRECT: Stay current with recommended updates to your operating system. These updates improve functionality of 
applications, remove security risks, and automatically resolve performance issues solved from bug reports.`

#### Sentence Formation

Keep sentences as short as possible. Cutting unnecessary words is vital to strengthen meaning. There are a number of common traps technical writers fall into resulting in lengthy sentences.

##### Indirect Discourse

Indirect discourse refers to the use of "that" to attribute a statement, fact, or feeling in a sentence without the use of quotation marks. In regular writing, it weakens statements of fact. Documentation writers can improve the impact of sentences by removing "that" and "which."

`INCORRECT: Mandriva is an open source operating system that is upstream for many other open source projects.`

`CORRECT: Mandriva is an upstream open source operating system for many other open source projects.`



##### Other Unnecessary Word Combinations

Avoid using the unnecessary word "then" following an "if" statement.  When a sentence begins with an "if" statement, follow it with a comma and complete the sentence with a full statement.

`INCORRECT: If an email client will not send or receive messages, then check under the File Menu and verify "Work Offline" mode is unselected.`

`CORRECT: If an email client will not send or receive messages, check under the File Menu and verify "Work Offline" mode is unselected.`

Many words we use in everyday conversation reduce impact in printed materials because they "leave a way out." These are words preceding verbs and nouns to minimize the sentence's influence. This is not an exhaustive list, but mindful documentation writers will reduce using these words and those of a similar nature.

##### Avoid Reducing Impact With Unnecessary Words
''The following words minimize the impact of the verb or noun clause within a sentence. Other words also fit into this category, but this short list is aimed at helping documentation writers identify words of this nature and eliminate them from their writing:'' 
'''should, could, may, might, perhaps, some, many, most, numerous, few, somewhat, whatever, possibly, can, occasionally, and frequently.'''


##### Sentence Variation
For the strongest impact, keep the first and last sentences of a paragraph as short as possible. Varying sentence length within a paragraph and through the entire document keeps a reader's attention. A short and simple fact is easy to grasp and use to analyze the next sentence's topic. There is nothing wrong with using longer sentences to explain complex ideas and concepts. Try to use a simple synopsis sentence at the end of each paragraph to give readers a reprieve and recap of any important information. A short final sentence stays with the reader to the next section.

#### Capitalization

In sentences, capitalize the first word.  Do not start sentences with a command, package, or option name.

`INCORRECT: <code>smolt</code> provides hardware profiling.`

`CORRECT: The <code>smolt</code> package provides hardware profiling.`


In headings, always capitalize the first word regardless of the type of speech. All subsequent words are also capitalized other than articles ("a," "an," or "the"), short prepositions ("in," "of," "for," "with," "at," "on"), or  conjunctions ("and," "but," "or").  

Examples:
* Avoid Using Contractions in Technical Writing
* Try to Do the Right Thing
* Find the Right Way to Say What You Mean
* The Grass is Always Greener on the Other Side of the Fence

#### Punctuation

Punctuation is a crucial component of understanding prose. A misplaced comma, period, or an improper punctuation mark changes a sentence's meaning entirely. Punctuation marks are the fasteners in a writer's toolbox. Readers are accustomed to the regular nails and screws, like commas and periods. Start throwing in lots of flashy hinges or braces like semicolons or ellipsis, and the unfamiliar notations easily distract readers. Complex punctuation marks are not universal, hindering translation efforts of OpenMandriva Documentation.

Minimize the following punctuation marks in documentation:
* Parentheses or "em dashes".
To compensate, rearrange the sentence, or break it into two complete thoughts.
* Semicolons
Good to use only if two thoughts are related, must be joined for clarity, and removes the need for a conjunction.
* Colon
If there are more than three items, use a bulleted list for easy comprehension.
* Ellipsis
Do not use for stylistic emphasis... only to denote an indefinite continuation of content in an example.
* Exclamation points
In technical writing this is accepted for use only as a most dire "warning" admonition, not for emphasis.
* Ampersands
The word "and" is to be written out, and this mark only reserved if it is part of a computer command.
* Slashes
Do not use slashes for a short hand version of "he or she" by using he/she, instead use the words "and," "or," or "either." Slashes are commonly used in file paths and using them otherwise will create confusion.

### Other Writing Questions

Every writer hits writing obstacles. It becomes difficult to adequately phrase something, or the words just do not "sound right." This is why the Openmandriva Project is a team effort. Call on fellow documentation writers in the mailing list or chat room for help with wording and formatting issues. Another trick professional writers use everyday is time away from the project. Take a break away from the document. Returning to a troublesome spot with fresh eyes is often all that is needed to overcome the writing hindrance.

The overall goal of the OpenMandriva Documentation Project is to provide assistance to OpenMandriva users in easy-to-understand language. You do not have to write to impress an English professor, or show off your expertise in a subject matter. Short sentences, frequent definitions of new and unfamiliar terms, and reference links are all aids our audience appreciates most. Write with your target audience in mind, and it will be your documentation contributions with the highest visits of users in need of answers.


----
*Credits:
Taken from* [Fedora Project Style Guide](http://Fedoraproject.org/wiki/Docs_Project_Style_Guide_-_General_Guidelines)


