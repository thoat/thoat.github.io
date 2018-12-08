# Reminders of software best practices

More like a _note-to-self_, this file contains (pseudo-)principles or drops of wisdom that I've heard of, mostly from the Internet, on good practices that programmers should follow - for the sake of their software's quality and the sake of humanity.

Of course, this list reflects my maturity as a programmer too. That is, via ideas that seem plainly obvious to most developers but sound significant enough for me to record here, one can guess my experience level.

## Testing

> if you’re __thinking about your test cases before writing your code__, then you start developing with __a clear idea__ of what your code needs as __input__ and what it produces as __output__

(Credit: [Simple Programmer: 5 Tips for Code Quality](https://simpleprogrammer.com/5-tips-code-quality/). Bold format added)

__!!__ Have proper tests in place before doing any refactoring.

## Performance

> When programming at a very high level - where all of the computation, networking, parsing, etc., are performed using libraries not written by yourself, knowing the performance figures of low-level operations may not help much, since your opportunity to improve each library's performance is rather limited or outright impossible.

> Instead, read the performance-related documentation of each library carefully. If a library does not come with those, ask them - make it an issue. Or __learn how to benchmark software__ in the correct way.

(Credit: [this answer on StackExchange](https://softwareengineering.stackexchange.com/a/312548). Bold format added)
