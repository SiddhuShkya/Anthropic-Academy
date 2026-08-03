# Project Overview — Building a Reminder Tool

**Goal:** teach Claude to set time-based reminders through tool implementation in a Jupyter notebook.

**Target interaction:**
> User: "Set a reminder for my doctor's appointment, a week from Thursday."
> Claude: "I will remind you at that point in time."

## Three Core Problems Requiring Tools

1. **Time knowledge gap** — Claude knows the current date, but not the exact time
2. **Time calculation errors** — Claude sometimes miscalculates date arithmetic (e.g. adding 379 days to a date)
3. **No reminder mechanism** — Claude understands the *concept* of a reminder but has no way to actually implement one

## Three Corresponding Tools

1. **Current datetime tool** — gets the current date + time
2. **Duration addition tool** — adds a time duration to a datetime (e.g. current date + 20 days)
3. **Reminder setting tool** — actually sets the reminder

## Implementation Approach

Build one tool at a time, working toward multi-tool coordination.
