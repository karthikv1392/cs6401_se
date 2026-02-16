---
layout: page
title: Project 2
permalink: /projects/project-2
parent: Projects
nav_order: 2
---

# CS6.401 Software Engineering 
## Spring 2026

## Project 2

---

> The software isn’t finished until the last user is dead. - *Sidney Markowitz*

Welcome to the second project of the **CS6.401: Software Engineering** course! Good job *rolling* with the Apache Roller, by now you must have a decent idea about the system, having reverse engineered it’s design and identified areas for improvement (~~you now know which files to provide as context to an LLM~~). 

This project focuses on extending and enhancing the Apache Roller with new features. You have to take care of SE design principles while developing these features. You have to keep modularity, maintainability and extensibility in mind while developing these features. You need to integrate **at least five design patterns** across different features with strongly backed justifications of why they have been used, referring to improvements across various Quality attributes and the trade-offs incurred with the same. 

*Note: When using Large Language Models (LLMs) or other AI assistants like ChatGPT, Claude, etc., in completing this project, kindly include screenshots delineating the specific prompts employed and the corresponding generated responses. Additionally, provide an evaluation of the accuracy of these responses, highlighting instances of correctness or errors.*

*In case it wasn’t clear already, you must build upon the refactored codebase that you had submitted for Project 1.*

### Github Classroom

You will be continuing to work on the same repository that you used in the first project. Please **make a new branch** for this project named `project2_<team_id>`. **Only this new branch will be considered for evaluation.**

---

## Project (100 Marks)

You are going to upgrade the Roller. The interactions will be better, more structured and integrated with LLMs to keep up with the hype ~~(it’s not a bubble until it bursts!)~~. Keep the codebase clean and efficient, while extending it. Don’t make it a nightmare to work further on the features you implement today. Continuing last year’s tradition, we found ourselves once again pouring our late-night ramblings into this — italicized (*with due credit to last year’s SE TAs).*

---

## 1. User Highlights

### 1A Stars (5 Marks)

*How does it not make sense to have a like button for my blogs? I just love the content that some of these bloggers are making, and want to be caught up with their posts so that I can be considered a “real” fan!*

Let users visit blog pages and "star" (favourite) them. From their home page, they should be able to look at all their starred webpages and visit those webpages. These webpages must be sorted in order of when the most recent blogpost was made (recently updated webpages must be at the top of this list), and you must also display the date (and time) of when the webpage was last posted to. Note that we only require you to consider the recency of blogposts themselves, and NOT the comments.

Additionally, they should also be able to "star" blogposts.

### **1B Trending Blogs (5 Marks)**

*I NEED to know what’s trending cause I have a ton of FOMO.*

Highlight the top 5 trending blogposts and blog pages based on the number of users who have liked (starred) them. Efficiency is of the utmost importance here, **Do not** iterate over individual articles here (you won't be awarded full marks for this part if you do so). You must optimize the way you fetch this information.

---

### 2. Transforming Feeds (10 Marks)

*So anybody can post anything, and it’s upto the poor souls who maintain the page to actually sit and go through all new blogs with no control? Nope, I would rather automate my work, thank you very much.* 

The goal is to allow filters and pre-processing steps to be added without breaking the existing pipeline.

Currently when a blog is posted we don’t have much control on the kind of filters and controls we want to establish on the content. This is not good. We want to bring in potential for censorship (definitely no political propaganda in mind whatsoever) and other pre-processing steps. A posted blog should go through **at least 3 steps (it is up to you to decide what those are, be creative!)**, including but not limited to profanity filters, text summarisation to reduce blog length to a fixed max word count, and generate tags using another step (these tags need not be stored separately, can be added in the body of the blog). Note that you are free to use LLMs or static rules for this. An important thing you’ll have to consider is that we should be able to add/remove steps without it affecting the remaining process! 

(Hint : Play around with roller, you might find some controls in the settings. The only thing to keep in mind is that the controls mentioned in this feature are **admin-side,** NOT user-side. You might find some helpful components like the Summary and Spam filters which *might* work with your implementation, though it is not necessary to stick to them).

---

### 3. Bug Reports (15 Marks)

*Users should be able to report broken buttons, links etc. The site needs to improve itself and for that, real user feedback is important.*

Users should be able to submit issues within the Roller, be creative in your definition and composition of an “issue”. The admin will have access to a bug dashboard, where they can view, mark bugs as resolved, or delete irrelevant reports. Users should also be able to delete their reported bugs. To make life more painful for the admins (imagine SE TAs to be the admins), whenever a bug is lodged/modified/deleted, they should be notified using an email. You are free to use any email account of your choice. Look up [MailerSend](https://www.mailersend.com/features/email-api) or other APIs for this. Also, a user should receive emails of their bug status on their registered email address. 

Additionally, the system that you come up with should be modular enough to support the addition of new notification channels (e.g a Slack Webhooks or MS Teams Integrations) without any impact to the remaining notification channels. We are NOT asking you to implement these, just keep this in mind while coming up with a design (and justify HOW your design facilitates the addition of new notification channels without much fuss).

---

### 4. Admin Dashboard (15 Marks)

*Building on the bug report, admins want to monitor the website data. However, they are very busy people and hence they don’t always have the time to look into the details. For this reason, they would love support for different views; some compact, some elaborate.*

Administrators currently lack a centralized way to track site engagement. To solve this, you need to implement a **Site Summary Dashboard**. This dashboard must be capable of showing the total number of users, the top-performing category, the most starred blog, and a leaderboard of the top 3 most active users (or any other metric you find useful and trackable; implement **atleast 5**). The admin should be able to toggle between two distinct modes: a **Minimalist View**, which constructs a basic report containing only the user count and top category, and a **Full View**, which assembles the entire suite of metrics. **Definition of each view shouldn’t be described with the logic to fetch data, so that one can flexibly modify what and what not to include in each view.** 

**Note:** You are free to choose your own metrics and definition of views, but they should make sense (to you and also your evaluating TA, so decide carefully!)

---

### 5A. Web Translation (20 Marks)

*Language shouldn’t be a barrier for posting stuff online; we want to read articles of other languages as well. And this is exactly what **you** need to ensure now.*

Remember how you open up a page in some random language and Chrome (or any other browser) automatically detects the language and allows you to translate the blog in the language of your choice? You’ll be doing exactly that. The only difference is that this is **application-sided, not browser-sided.** When a user triggers translation, the text that’s already on the page should be translated to a language of their choice and shown back to them **in place of the previous text** (just like how Google Translate does it, for example). The page shouldn’t break, the layout shouldn’t change, and images, links, etc. should remain as they are. Only the text changes. You can use *any* translation approach you want: API calls, MT models, LLMs, etc., however, we want you to provide support for one model from [Sarvam AI](https://www.sarvam.ai/) and use another from either Sarvam itself or any other provider. You also need to support **at least two different ways of translating** (one of which is the Sarvam AI way, and no, using 2 models from Sarvam does NOT count as two different ways of translating). The translation provider should be easily switchable. 

What *isn’t* open-ended is that you must support **at least five languages**, and any language you support should work both as a source and as a target.

### 5B. Caching :D (15 Marks)

*It doesn’t make sense to bombard Sarvam AI with 100s of API calls for stuff you have already translated. A real software system must allow scaling user requests for a feature while not exhausting their API credits!*

Translations must be cached after the first successful translation of a page. When a user revisits the same page, the system should reuse the cached version and automatically translate the webpage using their last used configuration (destination language, translation provider etc.), if there are no significant content changes. What constitutes a “significant change” must be clearly defined (e.g., modifications to primary content such as article body or headings). If significant changes are detected, only the affected sections should be invalidated and retranslated, while unchanged sections reuse their cached translations. Full-page retranslation should be avoided unless demonstrably more efficient (in terms of time/latency, cost, etc.). Real-time user input does NOT need to be translated; only content present at page load must be processed.

---

## 6. Community Pulse Dashboard (15 Marks)

*Some of us might like to endlessly scroll comment sections. For those of us who don’t; i.e. for authors trying to make sense of reader feedback, we need a Community Pulse Dashboard that helps weblog authors easily understand what their readers are talking about, just like how platforms such as YouTube now use AI to group and summarise comment topics so creators can quickly see what discussions are about instead of reading every single comment.*

In this feature, you will extend Apache Roller with a **Community Pulse Dashboard** that summarizes and organizes comment discussions. While LLMs can help, they are resource-intensive, so your design should balance lightweight methods with selective AI usage.

### 6A Discussion Overview (5 Marks)

*First let’s start with the simple old-school stuff.*

For each weblog entry, authors should be able to view a high-level snapshot of comment activity through **multiple lightweight overview indicators**. Examples of such indicators include (but are not limited to):

- how active the discussion has been
- the kinds of responses being posted (questions, feedback, debate, etc.)
- recurring points or concerns raised by readers

**You must implement a minimum of three such indicators** (the above list provides possible examples, but you are free to define your own as long as they are meaningful).

This component should rely only on **classical, computationally inexpensive methods** *(such as keyword frequency analysis or basic statistical measures), with no LLM/DL involvement.*

### 6B Conversation Breakdown (10 Marks)

*Now, let’s add some AI into the mix. The system should generate a short, readable summary that helps authors quickly understand what readers think about their writing, without having to sift through every single comment. That said, be mindful of your LLM API calls; while these models may help you finish assignments faster than ever, they also come with real computational and environmental cost. Use them wisely, not blindly.*

The system should provide an organized breakdown of the comment section, including:

- a small set of major themes being discussed
- representative comments for each theme
- a short recap of the overall conversation

Think carefully about what parts of this pipeline require heavier AI involvement, and what parts can be handled through simpler, more efficient techniques. (be creative!)

The design should allow the system to **easily switch between multiple insight-generation methods depending on available resources**.

**At least two distinct methods must be implemented**, and LLMs should be used **only when necessary**. Again, do NOT use a nuke to kill a fly!

*Note: You are free to use services such as Gemini AI Studio or GroqCloud for LLM API access. Both platforms provide free, albeit rate-limited usage.*

**Note: Evaluation will heavily consider the degree to which the design patterns are applied (as long as they make sense), rather than simply completing the implementation in any manner.**

---

## **Bonus: Weblog Q&A Chatbot (5 Marks)**

*Sometimes users don’t want to browse dozens of posts — they just want answers. Wouldn’t it be nice if Roller could answer questions like “What has this blog said about data privacy?” or “When was topic X last discussed?”*

In this feature, you will implement a Weblog Q&A Chatbot that allows users to ask natural language questions about a weblog’s entire collection of entries and receive grounded answers based on those posts.

Your solution must support **at least two distinct answering strategies**, including but not limited to:

- **Long Context Input** — directly passing large portions of weblog content into a model capable of handling extensive context.
- **Retrieval-Augmented Generation (RAG)** — retrieving relevant passages from the weblog archive and using them as input to a generative model.

You should integrate the chatbot into the Roller UI so that users can interact with it on a weblog page and ask questions grounded in that weblog’s content.

In your project report, you must compare the approaches you implemented and discuss the practical trade-offs observed as the weblog size grows and different query types are posed, with concrete observations and reasoning based on your implementation.

*Note: This bonus will only recoup marks lost in this project. It will not add to your course total, i.e. your project 2 marks will be min(100, project marks + bonus).*

---

## **Submission Instructions**

- The submission for this phase will again be through the GitHub classroom. **The codebase will be automatically downloaded at the deadline**, so ensure that everything is up in time. No exceptions will be granted.
- You need to submit a report containing the details of implementation, including the design patterns used, the rationale behind using the pattern and any changes made to existing code. The report should be present in the `docs/` directory, titled `project2_<team_number>.pdf`.
- If you are attempting the bonus, please make a separate branch and a separate document titled `project2_bonus_<team_number>.pdf` in the `docs/` directory.
- Report the contribution of each team member at the end of the report. This will be considered when evaluating the project.

---

## Deadlines

Soft deadline - 15th March, 2025 11:59PM IST

Hard deadline - 22nd March, 2025 11:59PM IST

***Note: Bonus can be submitted till the hard deadline without any penalty. Late days are not applicable for bonus components***

To encourage consistency, at least 50% of your total commits must be made before the last week of the soft deadline (15th March), i.e., 50% commits should be made before 8th March 2026, 11:59 pm. Repositories showing most of the work being done close to the deadline may be penalized.

The course policy mentioned on this website will be followed for late submissions and associated penalties/late days.

---
