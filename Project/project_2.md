---
layout: page
title: Project 2
permalink: /projects/project-2
parent: Projects
nav_order: 2
---

# CS6.401 Software Engineering 
## Spring 2025

## Project 2

---

Welcome to the second project of the CS6.401 Software Engineering course project! In the first project, we analyzed the Rudra’s Subscription Service (RSS) Reader system, reverse-engineered its design, and identified areas for improvement. Now, in this project, we will focus on extending and enhancing the RSS Reader by introducing new features while applying software engineering principles.

This phase focuses on effective design practices to ensure modularity, maintainability, and extensibility. You are required to integrate **at least five design patterns** across different features. The frontend modifications need not be intensive and are not the focus. 

*Note: When using Large Language Models (LLMs) or other AI assistants like ChatGPT, Claude, etc., in completing this assignment, kindly include screenshots delineating the specific prompts employed and the corresponding generated responses. Additionally, provide an evaluation of the accuracy of these responses, highlighting instances of correctness or errors.*

### Github Classroom
You will be continuing to work on the same repository that you used in the first project. Please make a new branch for this project named `project2_<team_id>`. Only this new branch will be considered for evaluation.

---

## Project (100 Marks)

_The RSS Reader is about to get a serious upgrade. Forget the days of staring at an unfiltered sea of content and manually picking out relevant articles. This time, we’re making the system smarter, more structured, and easier to use. You need to extend the RSS system by introducing new capabilities while keeping the codebase as clean and efficient as possible._

The project is worth a hundred marks (well, if it weren't, we would just scale it, duh). To make things interesting, we have decided to add in our ramblings at 2AM (italicized) followed by the actual technical asks.


### 1. User Registration (10 Marks)

_First things first, let’s talk about user registration. Currently, signing up is a privileged affair—only the admin can create accounts. That’s changing. We don’t want our RSS Reader feeling like an exclusive club with a bouncer at the door._

Currently, only the admin can create accounts. That’s changing. Users should be able to register themselves through a registration system with username, password and everything else that's required. Make sure to add apt validation checks (emails should be unique, valid email id etc.)

### 2. Filtering by RSS Feed (10 Marks)

_Next, let’s refine how users interact with their feeds. Right now, they can either view everything at once or pick a single feed. But what if they just want to browse, say, technology updates from a few select sources? Filtering should be intuitive and allow users to refine their view based on categories or selected feeds. No more scrolling through endless lists of irrelevant news—just the content that matters._

The system should allow users to filter feeds by category or specific RSS sources or both. This will enable more personalized browsing and better content organization. Users should be able to set filters dynamically via UI controls, ensuring a seamless experience.

### 3. Bug Reporting (15 Marks)

_Bug reporting also needs an overhaul. At present, reporting an issue whisks users away to GitHub. While that’s great for developers, it’s not the best user experience._

Users will be able to submit issues within the RSS Reader itself - to make things simpler an issue is just a statement (description) with a timestamp. The admin will have access to a bug dashboard where they can view, mark bugs as resolved, or delete irrelevant reports. Users should also be able to delete their reported bugs (We imagine a few of you would like to do that for the doubts you send us).

### 4. Making Categories Better (10 Marks)

_Speaking of organization, let’s make categories a little smarter. Right now, they’re flat and uninspired. We want nested categories, so users can group feeds in a structured way. A "Technology" category should be able to house not only direct feeds but also subcategories like "AI," "Blockchain," or "Cybersecurity."_

Categories should support nesting, allowing up to **5 levels** of subcategories. Each category (and subcategory) should display metadata such as the number of unread items and the total count of articles. The UI should render nested categories in a collapsible format. A category should be able to host individual feeds as well as subcategories (as in, a combination of both).

### 5. Custom Feeds (30 Marks)

#### **5A (15 Marks) Simulating RSS Feeds**

_Then there’s the problem of RSS feeds—or the lack thereof. Some websites refuse to provide an RSS feed, making life harder for users. We’re fixing that._

Some web pages lack RSS feeds. The system should extract content using APIs like [NewsAPI](https://newsapi.org/docs), format it as an RSS feed, and present it to the user. API calls should be optimized to minimize request overhead.

#### **5B (15 Marks) User-Created Feeds**

_But why stop there? Users should also be able to create their own custom feeds. Imagine picking favorite articles from different sources and bundling them into a single feed. Better yet, other users should be able to subscribe to these curated selections, turning the RSS Reader into a personalized content-sharing platform._

Users should be able to curate their own feeds by selecting articles from multiple sources. Other users should be able to subscribe to these curated feeds. Do note that users should also be able to add articles extracted from the sub-section directly above.

### 6. LLM-Features (25 Marks)
You are expected to use OpenAI/Gemini/comparable APIs for this task. OpenAI provides 5$ worth of free API usage to every user, and Gemini offers free API usage with a rate limit. See respective websites for more info.

#### **6A (20 Marks) Daily Report**

_Now, let’s add a dash of AI. Daily summaries should be generated for each user, neatly compiling the latest updates from their subscriptions. But not all content is equal—feeds directly within a top-level category should carry more weight than those buried inside subcategories._

A **daily report generator** should summarize the latest updates for each user’s subscriptions. Feeds within a category should be weighted more heavily than subcategories - think of creative ways to do this. The system should format summaries in a structured way for easy readability.

#### **6B (5 Marks) Duplicate Detection**

_And while we’re on the topic of automation, let’s introduce duplicate detection. If two articles are essentially the same, we should be able to tell._

The system should be able to detect duplicate articles using simple techniques such as Named Entity Recognition (NER) and keyword-based similarity matching or semantic matching (your call). The implementation should avoid excessive computation and storage overhead. We expect the user to select the two articles for comparison in this task.

_**Note : Evaluation will heavily consider the degree to which the design patterns are applied, rather than simply completing the implementation in any manner.**_

---

## Bonus (10 Marks)

### Top News Items

_Finally, for those who love staying on top of trends, let’s highlight the most popular news items._

The system should highlight the **top 5 trending articles** based on the number of users who have liked (starred) them. Efficieny is key - avoid iterating over individual articles to get full marks. Some possible optimizations could be leveraging the  schema or external caching mechanisms (feel free to use any other mechanism). 

_Note: This bonus will only recoup marks lost in this project. It will not add to your course total, i.e. your project 2 marks will be min(100, project marks + bonus)._

---

## Submission Instructions
- The submission for this phase will again be through the GitHub classroom. The codebase will be automatically downloaded at the deadline, so ensure that everything is up in time. No exceptions will be granted.
- You need to submit a report containing the details of implementation,
including the design patterns used, the rationale behind using the pattern and any changes made to existing code. The report should be present in the `docs/` directory, titled `project2_<team_number>.pdf`. 
- If you are attempting the bonus, please make a separate branch forsubmit a separate document titled `project2_bonus_<team_number>.pdf` in the `docs/` directory.
- Report the contribution of each team member at the end of the report. This will be considered when evaluating the project.

Soft deadline - 15th March, 2025 11:59PM IST

Hard deadline - 22nd March, 2025 11:59PM IST

_**Note: Bonus can be submitted till the hard deadline without any penalty. Late days are not applicable for bonus components**_

The course policy mentioned on this website will be followed for late submissions and associated penalties/late days.

---

## Doubts Policy
Please post all your relevant doubts on Moodle rather than emailing the project TAs (Shashwat & Vineeth) individually.

