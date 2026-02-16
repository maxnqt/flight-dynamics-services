# Onboarding

- Rule of thumb: Expect to be a solid contributor on a new team after 3 months
- Great onboarding process has:
  - Up-to-date wiki on setting up your dev environment
  - Async support channels (e.g. Q&A groups, eng chat threads) to get small technical questions answered
  - Backlog of unambiguous, low-risk tasks

## Navigate a new team

- Find someone on the team: Ask for 30 minutes with them (ask manager for initial list of names)
- For the first 25 minutes: Ask them to tell you everything they think you should know
  - _Learning team direction: "What is the motivation behind your work?," "How does this fit into the team's plan?," "What wins are we expecting from this?"_
  - _Learning system design: "Where does your work fit into the overall system?," "What pieces does our team own?"_
  - _Learning who knows what: "Who knows the most about <area>?," "If <area> breaks, who knows how to fix it?"_
- Take notes, stop to ask about things you don't understand
- For the next 3 minutes: Ask about the biggest challenges the team has right now
- For the final 2 minutes: Ask who else you should talk to; write down every name they give you
- Repeat until you aren't given any new names

## Contribute code fast

- Immediate priority: Start landing code, get a high-level understanding of the codebase
- Goal: Get comfortable making changes
- Example approach: Land lots of low-risk changes (~1-2 per day) that improve the codebase

## Learn the codebase

- Get the code working on your machine
- Check what tech is used: Familiarise yourself with at least the major ones from here via their "quick start" or basic documentation (dive deeper as you work on the codebase)
- Understand the overall structure: Start at the main entry point and follow the path the data takes, figure out what parts of the code are invoked; then debug and do line breaks as you step through the code
- Set up and run the tests
- Be hands-on: tackle small, well-defined tasks
- Understand the system: "Which services work together?," "What goal are they trying to achieve?," "How are each of the services deployed/run/accessed?," "What's the development workflow for each?"
- Read available documentation carefully (for any documentation related to the team's stack [e.g., Django], make sure to read the documentation for the correct version)
- Understand the high-level areas: Start with the different components, then the subdirectories, then the classes and their relations and so on; build an intuition for how everything works
- Understand the functionality: "What will this function return if I give it <input>?," "How can I summarize what this method is made to do?," "What are some potential gaps in the existing tests for this method?"
- Understand design patterns: Identify the name of the design pattern that was implemented; understand the intention and the meaning of abstractions
- Analyize telemetry and metrics: Study metrics to understand how the system behaves in production, what patterns emerge during peak usage, and which components require the most attention
- Explore through testing: Make deliberate modifications to the code, observe their effects; write new tests to verify understanding; intentionally break things (in development) to see how the system fails (_build an intuitive understanding of the application’s boundaries and failure modes_)
- Pair program: Ask questions about their workflow, note which files they frequently access, get to know their debugging strategies
- Understand the "why": Dig deep into the motivation behind tasks; understand the business context and technical reasoning; ask (seemingly basic questions)
- Monitor team communications: Stay active in ncident response discussions, pay special attention to production alerts and how the team responds to them
- Create personal documentation: Maintain a living document of your discoveries, questions, and insights; document important code paths, architectural decisions, and system interfaces as you encounter them
- Build technical maps: Create diagrams of system architecture, data flows, and entity relationships; start with high-level “black boxes” and gradually fill in the details as your understanding grows
- Maintain a command cheat sheet: Keep track of useful commands, scripts, and workflows you discover; include context about when and why to use them
- Gather information on the domain: Important for understanding of a codebase is to have a deep understanding of the domain
- Write internal guides: Once you learn something new, document it for the next person
- Contribute to official documentation: When you find gaps in the existing documentation, take the initiative to improve it
- Regularly reflect on your learnings:
  - Can you describe the system in a few concise sentences?
  - How does it interact with adjacent systems?
  - What surprised you most during the learning process?
  - What aspects remain unclear?
 - Code base discovery template: [https://gist.github.com/brittanyellich/262d8d94d8b80cfd9ec5dad677d2fef8](https://gist.github.com/brittanyellich/262d8d94d8b80cfd9ec5dad677d2fef8)
 - Documatic code search engine: [https://marketplace.visualstudio.com/items?itemName=Documatic.documatic](https://marketplace.visualstudio.com/items?itemName=Documatic.documatic)
 - GitLens code authorship visualization: [https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

---

Approaches you might consider:

Try to find out what the code is supposed to do, in business terms.
Read all the documentation that exists, no matter how bad it is.
Talk to anyone who might know something about the code.
Step through the code in the debugger.
Introduce small changes and see what breaks.
Make small changes to the code to make it clearer.
Some of the things I do to clarify code are:

Run a code prettifier to format the code nicely.
Add comments to explain what I think it might do
Change variable names to make them clearer (using a refactoring tool)
Using a tool that highlights all the uses of a particular symbol
Reducing clutter in the code - commented out code, meaningless comments, pointless variable initializations and so forth.
Change the code to use current code conventions (again using refactoring tools)
Start to extract functionality into meaningful routines
Start to add tests where possible (not often possible)
Get rid of magic numbers
Reducing duplication where possible
... and whatever other simple improvements you can make.

---

First-week triage

Effective learning techniques

Code reading patterns
Read from public APIs inward, not file-by-file. Identify core abstractions and variant implementations.
Use IDE + structure map: call hierarchy, find usages, and type hints.
Use tests as documentation
Unit/integration tests often reveal intended behavior. Add tests when behavior is ambiguous.
Version-control archaeology
Read relevant commits and PR discussions to learn why things were implemented a certain way.
Contributing safely and quickly

Make atomic, well-scoped changes
One logical change per PR, clear description, and link to related issues or design docs.
Include tests and migration steps
Demonstrate correctness and upgrade path for runtime or DB changes.
Use feature flags and canary releases
Deploy changes behind toggles to reduce blast radius and enable gradual rollouts.
Respect the review process
Incorporate feedback promptly and explain trade-offs in PR descriptions.
Refactoring and larger improvements

Prove before you refactor
Add tests around the area, write benchmarks for performance-sensitive code, and measure before/after.
Break work into incremental, reversible steps
Replace modules piecewise, keep compatibility layers, and avoid cross-cutting changes in one PR.
Define success criteria
Performance, test coverage, clarity, and maintainability metrics. Use these to justify larger efforts.
People and process

Build trust through small wins
Fast, correct PRs with good tests and documentation accelerate trust.
Pair with domain experts
Pair-program or do code walkthroughs with long-tenured peers to capture tacit knowledge.
Share discoveries
Add or improve onboarding docs, diagrams, and runbooks as you learn.
Advocate for tooling improvements
CI, linting, reproducible dev environments, and error dashboards pay long-term dividends.
Avoid common pitfalls

Don’t refactor blindly: large cosmetic changes make review and blame hard.
Don’t assume intentions: historical constraints often explain ugly designs.
Don’t shortcut tests or CI: they’re the safety net for a complex system.
Don’t push big changes without stakeholder alignment and rollout plan.
Sample 60/30/10 plan (first 90 days)

60% learn and stabilize: run, trace, fix small bugs, improve tests, ship small PRs.
30% improve: address recurrent pain points, add monitoring, incrementally refactor with tests.
10% lead: propose larger changes, design documents, or process/tooling improvements backed by data and prototypes.
Outcome expectations

After 2–4 weeks: local setup, several small PRs merged, basic end-to-end understanding.
After 2–3 months: ownership of a service or subsystem, contributions to reducing debt, credible proposals for larger improvements.
Practical checklist to carry with you

Can I run the app and tests locally in under X minutes? (measure)
Where are the runtime errors and alerts concentrated?
Which modules have the fewest tests and most bugs?
Who approves changes for each area?
What are the deployment and rollback steps?
Adopt a mindset of cautious curiosity: learn the system by using it and changing it in small, observable increments, build trust through dependable contributions, and scale improvements only after understanding the risks and adding safety nets.

---

0. Understanding a codebase:
0.0. Get to know the codebase:
0.0.0. Code distribution:
You can get an overall "idea" of the code distribution, or where the meat is, by using `cloc . --by-file`. This shows you a listing of files and their respective number of lines of code and comments. You instantly get an idea of the "big" files of the project you probably should get to know.
You also see the ratio comment/code and can start documenting and writing tests as you go. It will help you understand the project, and will be useful for everyone and in refactoring.
0.0.1. Structure:
0.0.1.0: Visualization
Drawing helps me. Conceptual blocks of the project. It can start as block names and boxes "Codec", "Streaming", "Persistence", "Dispatcher", etc.
Drawing on paper, whiteboard, etc. You can also use something like "Gliffy" to diagram for yourself and with someone when communicating. You can both change and make sure you're talking about the same thing.
And do it going down the abstraction scale. Higher abstractions to lower abstractions.
I also found a quick automatically generated "UML" diagram helps. I don't write them necessarily, but I use a tool that tells me about the structure of a project.
pyreverse for Python, scaladiagrams for Scala, are just a few examples that generate an image you can save and glance over after the `cloc` stuff.
0.0.1.1: Grep
I use `git grep` on the classes found in the biggest files I found with `cloc`. I can see how they "disseminate" through the project and how they get around and are used
0.0.1.2: Tests
I look at unit tests (if any) to get a sense on what the different parts do and how they're used. You learn a lot about "intent" from the tests if you're lucky to have them. I add tests as I get acquainted with the project.
If there's a CI config file, I'll check it out and it tells me how to deploy the project. It's often more accurate than the readme or else the builds would fail.
0.0.2: Musing
I maintain a separate "musing" file, sometimes called "refactoring" where I'll put a comment with the path to a file and the part it's about (say a function, or a class), and rewrite it. It is separate in the beginning as I don't know if the refactoring is relevant or if there's any Chesterton's Fence and I don't want to pollute the repo. It is my way of grappling with the code. Several rewrites. Often when I'm in a quiet place and my juices are flowing.
0.1. Taking notes for project:
One of my habits from the beginning was taking notes. I can now pull my notebooks at my current job and see the chronology (dated by month) and ordered. I can walk through the different difficulties, conceptualizations, drawings and schematics, sequence diagrams, re-architectures, refactorings, etc.
As you embark on your journey in a project, your fresh eyes are valuable. You're seeing a lot of what has become "normal" for other developers. Note everything. The idiosyncratic build or deployment. Out of date documentation. Everything.
You can create well written issues that follow a template with expected and actual behaviors, screenshots, logs, stack traces, possible fixes, likely culprits, etc.. If your repo does not have a template for issue, propose one.
Write issues in a way to make them easier to fix for everyone. Your group can use your notes to rework an API or the user experience. You're also working to streamline future contributions for newcomers.
0.2. Knowledge Base
As your understanding of the project increases and you touch more and more parts, you can maintain a sort of knowledge base. It is highly likely that this knowledge base will serve as the project documentation if it has none.
1. Attention
1.1 Taking meeting notes:
Many meetings. Few actions. Everybody ends up talking about the same things and issues drag on forever. You can take notes and review them later. Write them up and send them to everyone. Check out minutes of meetings.
You can write the gist of what's said, and the action that must be taken, by whom, and when.
Taking these notes will help mitigate your distraction during the meeting as you can review them at your rythm.
  # Minutes of Meeting
  --------------------
  
  ## Date: 2019-03-25
  ## Place: BIGCorp HQ. City, State.
  
  ## Participants:
  
  ### BIGCorp:
  
    - John Doe (jd)
    - MeMyself I (mmi)
  
  ### OtherCorp:
    - Dilbert (db@othercorp.com)
    - Dogbert (dg@othercorp.com)
  
  
  ## Topics:
  
    - Scheduled information sending
    - Information flow
    - Architecture for Project X
  
  ## Details:
  
  OtherCorp has raised some issues for the timeline of Project X...
  Blah blah blah.
  
  ## Actions:
  
  ### BIGCorp:
  
  - [ ] @bc: Send project X estimates by 2019-03-28
  - [x] @bc: Send invoice and cheque for offices remodeling
  - [ ] @mmi: Add different schemes for user authentication
  - [ ] @mmi: Finalize migrations so we take into account user's timezone
  
  ### OtherCorp:
  
  - [ ] @oc: Expose API end points for user's identity verification
  - [ ] @oc: Cache the results of the most common queries

2. Skills
Understand the business value for the customer (what value is your code bringing to the customer, what are they trying to achieve).
Daily improvements. Reading good books and implementing what they contain. Writing the best code you can write. Reading the best code you can find. Consistent, continuous, relentless, improvement.
If you can be better than you were when the day started, and do that daily, good things may happen.
Constantly transfer the quality gains to the projects you're involved in (better documentation techniques, better patterns, less complexity, etc.)
Help others write better code by setting the example. Mentor newcomers to the project. Help write tools for everyone to use.

---

Joining an existing team with a large codebase already in place can be daunting. What's the best approach;

Broad; try to get a general overview of how everything links together, from the code
Narrow; focus on small sections of code at a time, understanding how they work fully
Pick a feature to develop and learn as you go along
Try to gain insight from class diagrams and uml, if available (and up to date)
Something else entirely?
I'm working on what is currently an approx 20k line C++ app & library (Edit: small in the grand scheme of things!). In industry I imagine you'd get an introduction by an experienced programmer. However if this is not the case, what can you do to start adding value as quickly as possible?

--
Summary of answers:

Step through code in debug mode to see how it works
Pair up with someone more familiar with the code base than you, taking turns to be the person coding and the person watching/discussing. Rotate partners amongst team members so knowledge gets spread around.
Write unit tests. Start with an assertion of how you think code will work. If it turns out as you expected, you've probably understood the code. If not, you've got a puzzle to solve and or an enquiry to make. (Thanks Donal, this is a great answer)
Go through existing unit tests for functional code, in a similar fashion to above
Read UML, Doxygen generated class diagrams and other documentation to get a broad feel of the code.
Make small edits or bug fixes, then gradually build up
Keep notes, and don't jump in and start developing; it's more valuable to spend time understanding than to generate messy or inappropriate code.

---

Pencil & Notebook ( don't get distracted trying to create a unrequested solution)

Make notes as you go and take an hour every monday to read thru and arrange the notes from previous weeks
with large codebases first impressions can be deceiving and issues tend to rearrange themselves rapidly while you are familiarizing yourself.
Remember the issues from your last work environment aren't necessarily valid or germane in your new environment. Beware of preconceived notions.
The notes/observations you make will help you learn quickly what questions to ask and of whom. Hopefully you've been gathering the names of all the official (and unofficial) stakeholders.

## Credits

- [https://www.developing.dev/p/how-to-onboard](https://www.developing.dev/p/how-to-onboard)
- [https://boz.com/articles/career-cold-start](https://boz.com/articles/career-cold-start)
- [https://github.blog/developer-skills/application-development/how-github-engineers-learn-new-codebases/](https://github.blog/developer-skills/application-development/how-github-engineers-learn-new-codebases/)
- [https://stackoverflow.com/beta/discussions/77469060/how-do-you-quickly-learn-a-new-projects-large-codebase](https://stackoverflow.com/beta/discussions/77469060/how-do-you-quickly-learn-a-new-projects-large-codebase)
- [https://www.quora.com/How-do-you-deal-with-a-big-existing-code-base-when-you-are-new-to-the-team](https://www.quora.com/How-do-you-deal-with-a-big-existing-code-base-when-you-are-new-to-the-team)
- [https://news.ycombinator.com/item?id=19924100](https://news.ycombinator.com/item?id=19924100)
- [https://stackoverflow.com/questions/215076/whats-the-best-way-to-become-familiar-with-a-large-codebase](https://stackoverflow.com/questions/215076/whats-the-best-way-to-become-familiar-with-a-large-codebase)
- [https://stackoverflow.com/questions/214605/the-best-way-to-familiarize-yourself-with-an-inherited-codebase](https://stackoverflow.com/questions/214605/the-best-way-to-familiarize-yourself-with-an-inherited-codebase)
