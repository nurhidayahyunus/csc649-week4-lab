# Tech Stack Evaluation

## Project
WorkStudy Planner: a planner concept that helps working students avoid missed deadlines and schedule clashes.

## Requirements that drive the decision
- FR3: The system finds clashes between classes, tests, work shifts and deadlines.
- FR4: The system suggests a target finish date and study times that fit around work shifts.
- FR5: The system reminds the student one day before each test and deadline.
- NFR1: The clash result is shown within 5 seconds.
- NFR2: Only the dates and times of work shifts are stored, not employer details.

## Options
- Option A: Static web page on GitHub Pages (HTML and JavaScript). Data stays in the student's browser.
- Option B: Python web app (for example Flask) with a database on a cloud host.
- Option C: Chat bot (for example a Telegram bot) with a small cloud database and scheduled reminders.

## Decision matrix
Weight: 1 (not important) to 5 (very important). Score: 1 (poor) to 5 (very good).

| Criterion                            | Weight | A score | B score | C score |
|--------------------------------------|--------|---------|---------|---------|
| Fits my requirements                 | 5      | 3       | 5       | 4       |
| Skills I already have                | 3      | 4       | 4       | 2       |
| Time to build before my deadline     | 5      | 5       | 2       | 3       |
| Free hosting and tools               | 4      | 5       | 3       | 4       |
| Performance and security needs       | 4      | 5       | 3       | 3       |
| Room to grow later                   | 2      | 2       | 5       | 3       |
| **Total (weighted)**                 |        | 96      | 81      | 75      |

## Decision record
- **Context:** I need a tech stack for WorkStudy Planner, a planner concept for working students. I have a short time to build it, I want to keep costs at zero, and the data about work shifts is private.
- **Decision:** Option A, a static web page on GitHub Pages.
- **Reasons:** (1) It scored highest in the matrix (96 out of 115) because it is the fastest to build and the hosting is free. (2) It supports NFR2, because shift data stays in the student's browser and is not sent to a server. (3) It supports NFR1, because a static page loads fast, so the clash result can be shown within 5 seconds.
- **Consequences:** Easy: quick to build, free to host, and simple to deploy with my CI pipeline. Hard: a static page cannot send reminders when it is closed, so FR5 only works while the page is open. Data is also not shared between devices.
- **Risks and next review:** If reminders become the main need, Option C or B would fit better. The AI agent part of my concept would also need a separate service. What would change my decision: I did this check alone because I had no partner. If reminders when the page is closed become a must-have, I would choose Option C (chat bot) because it can send messages by itself.