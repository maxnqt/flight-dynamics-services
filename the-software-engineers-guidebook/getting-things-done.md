# Getting things done

- Realiably break down your work
- Realistic in your estimates
- Autonomous in unblocking yourself
- Deliver quality work

## Focus on most important piece of work

- **What is the most important work; the single most important task on your list?**
- **If you could only do one thing this week, what would it be?**
- Your answer is your #1 priority (identify it!)
- Make sure to definitely, absolutely deliver it within the agreed time frame
- Make a habit of always completing you #1 priority
- Even if it means turning down other tasks, skipping meetings, and pushing back on other matters

## Unblock yourself

- **Know when you're blocked:** You go more than 30 minutes (one hour at most) without meaningful progress
- Try different unblocking approaches:
  - Rubber-ducking: Explain your problem, approaches already tried to a "rubber duck" (**verbalize the problem**)
  - Sketch out the problem on a sheet of paper (**visualize the problem**)
  - **Read documentation and references:** Could you be using the tool in a way it wasn't designed for? Could you be neglecting features readily available to solve your problem?
  - Search online for similar problems: Describe problem in various ways, others might use different terms for same problem
  - Post a question on a Q&A site/forum (explaining the problem clearly could give you new ideas)
  - Take a break: Or switch to an unrelated task, come back fresh/with a new perspective
  - Start from scratch or undo all changes: Go back to the last point at which you were not stuck, restart, make small changes, one at a time
- **Get support to unblock yourself:** Contact others who could help, share knowledge, or connect you with others (_Hey, I'm stuck on this problem. Can anyone lend a hand, perhaps pair with me on it?_)

## Unblock yourself - cheatsheet

**Planning**

- Not enough clarity on what to do/missing information: Make clear what information is missing
- Not knowing who to reach out to for information: Ask for help from lead/manager, then make a list of points of contacts (consider sharing with team afterwards)

**Building**

- <mark>New language/framework: Find documentation, learn it, read source code, ask for resource recommendations (**start small; learn just enough to solve your problem before diving deeper**)</mark>
- Error messages: Try to solve it/figure it out, google it, pair with/reach out to a teammate, ask for fresh ideas
- Not knowing how something works: Decompose it by visualizing it,look at the source code, research; if you don't make progress, ask for help
- Build problems: Read up on the build tool, try to figure it out; contact person who set up the build, ask for pointers (_do the actual investigation work and make the fix_)
- Missing dependency: Let the other party know they're a blocker, excalate, pause work on the problem, try to come up with a workaround (involve your manager)
- Access problems: Contact your manager/senior colleagues, explain the problem/why you need access
- Misleading documentation: Contact the team who owns it, offer to fix it; make changes if you can modify the documentation (let the documentation owners know)
- Outages: Flag the outage and escalate it

**Testing**

- Tests fail non-deterministically: Debug and try to understand why, pair with a team member, ask in chat if anyone's had similar issues
- Missing test data: Figure out how to get this data
- Tests are too slow: Step up and look for ways to make tests faster, do some performance analysis of where slowdowns occur

**Reviewing**

- Waiting on code review: Ping reviewers to ask for reviews directly, escalate if you don't hear back in a reasonable time, seek support from team memebers and manager on how to handle
- Merge conflicts: Resolve the conflict, retest your work; **keep pull requests small to iterate faster, avoid merge conflicts**

**Deploying**

- Permissions/access problems: Find someone who can give access, escalate
- Deployment is too slow: Contact team/person who owns deployment tooling; tweak the deployment setup, get your hands dirty

**Operating systems and maintenance**

- Bugs that can't be reproduced: Seek more information (e.g., add extra logging)
- Not enough logs to debug system issues: Add more logs, monitoring, or alerts, and deploy them; pair with a teammate
- Outages: Alert manager and team, jump in to mitigate the outage

## Break down the work

- **Break down the work into small parts, then challenge yourself to make them even smaller**
- A good time to stop breaking things down: When the tasks are clear enough to you
- Begin at a high level: What are the main pieces of work? (_chunks_)
- Break the chunks down again (into tasks): Make sure resulting tasks are straightforward
- If needed, divide complex tasks into subtasks
- The easier to understand what needs to be done, the easier to estimate how long it will take
- **Prioritize work which gets you closer to shipping something:** Focus on an order of work that gets you closer to functionality (_the sooner you have something to test end-to-end, the sooner you can get feedback_)
- As soon as you have a basic, working case, decide the next priority and which tasks you need to solve to achieve it
- **Tasks are a tool for organizing work:** Be ruthless in changing and adding tasks as needed, removing redundant ones
- If you come across new work or run into blockers, overhaul the task

## Estimate the work

- Work similar to what you previously did: Estimate the time for the new task, based on how long it took last time
- Work similar to that of a colleague: Have them break down their approach, ask for/come up with an estimate, and add more time as you need to learn some of the context
- Refactoring: Ask yourself/teammates if they've done similar work, go based on that; _or_ timebox the work (work on it no longer than that)
- New work using a stack you know well: Refine requirements, if the task is clear, make a good enough estimate
- New work using a stack/system you don't know well: Consider prototyping first and making an estimate only when you've built a proof-of-concept; give an "ideal estimate" (assumes no issues), also provide a worst case estimate
- Building something simple with a stack you don't know well: Ask an engineer who's used the technology (where to start, the estimate); if possible, pair with a developer who knows the stack well; use a timeboxed estimate to get up to speed with the technology (_make timebox big enough for some tutorials, coding, first few iterations_)
- Building something complex with a stack you don't know well: Too many unknowns for a sensible estimate: You need to reduce the unknowns:
  - Make an estimate with learnings from a prototype, _or_
  - Break up the work more; separate into smaller parts, each of which only contains one unknown
 
## Seek mentors

- Don't think just in terms of one individual mentor, but a group of people/tribe of mentors you can learn from (diverse experience)
- Identify a dedicated mentor with whom you can discuss pressing issues regurlarly
- Also learn from ad hoc mentorship, experts online
- Aim to find mentors within the workplace whom you can rely on
- Schedule 1:1s with people whom you not work closely with, but whose work intersects with your path
- Internet mentors: Individuals who share their career journey and learnings on their blogs, books, podcasts, etc.

## Keep your "goodwill balance" topped up

- When you help others, your goodwill balance increases
- When you ask favors, it can go down
- **Take time to solve things yourself**
- Go through the most common debugging and information-gathering steps before seeking help
- Read the relevent document thoroughly first
- Look at the source code history and recent commits
- (Debugging) Step through the code, record variable values, note assumptions, do a structured analysis of where something is going wrong
- Don't ask too many trivial questions
- Ask good questions: Clearly explain the problem, summarize what you've tried so far, and what your next step would be if they cannot help
- **Make yourself available to others regurlarly; sit with them and solve their problems**
- **Share your expertise to make others' work easier**
- When someone helps you, and it solves your problem, thank them (in a public team setting)

## <mark>Take the initiative</mark>

- <mark>Consistently pick up smaller (or larger) pieces of work which were not asked of you</mark>
- Research a new technology to use on a project
- Talk with others, get involved in learning about other projects, offer to help out with smaller tasks
- Be the first to volunteer for any opportunity that arises (e.g., investigating a bug, giving a presentation)
- Examples of initiatives to help your team and yourself:
  - Document unclear things and share it with the team
  - Volunteer for investigations (ask/offer to pair with someone if your less experienced)
  - Inestigate interesting tools or frameworks your team could use; make a demo and share learnings with the team (even if the outcome is "we shouldn't use this")
  - Talk with your manager about upcoming projects, get a better sense of priorities and what's ahead (and express interest in work you're curious about)

## Credits

- Gergely Orosz, "The Software Engineer's Guidebook," 2024. [Online]. Available: https://www.engguidebook.com. [Accessed: Feb. 13, 2026].
