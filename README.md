

# Collatz Threads

The Collatz Conjecture is a seemingly simple math problem. We start with any positive integer, n.  If n is even, we divide it by two. If it's odd, we multiply it by 3 and add one.

Let's try 5. It's odd, so 3*5 + 1 == 16. 16 is even, so we divide by 2. 8 is even, we divide by 2 again. 4/2 is 2, 2/2 is one. We finish at 1, and it took five steps.

The Conjecture wonders if we can prove that every positive integer will eventually reach 1. Seems simple, but it's quite hard to prove!

Instead, let's write a program that implements the Collatz process on multiple threads, and try to learn to something about multi-threading along the way.

## Step One

We can write a program that that finds the number between 1 and 1 million that has the most Collatz steps. No threads, let's just find the answer.

## Step Two

Let's write the same program, but have it run with a number of threads between 1 and 16. The range of [1..1000000] integers should be divided amongst the threads as evenly as possible. Benchmark your program; what number of threads make it fastest? Make a spreadsheet that compares the timing of your program at each thread count. Compare that with the single-threaded program. Which is faster? Why?

## Step Three

Can we make our program even faster by having it avoid repeated work? In the above example, we find the Collatz count for 5 to be five steps. But along the way, we also solve 16 (four steps), 8 (three steps), 4 (two steps), 2 (one step), and one (zero steps). To your multi-threaded solution, add a lookup table that helps remember which steps have already been computed and skips to the answer if we're redoing work.  After computing 5, computing 8 should take no time -- its answer is already in the table. How does this alter the timings you discovered in step 2?

## Hints__

When writing Step One, how will you know your answers are correct?

When writing Step Two, how will you divide your work evenly among the threads? How will you know your answers are correct each time you run the program? How did you demonstrate that each of your threads is doing an equal-ish amount of work?

When writing Step Three, how will you make sure you make sure your lookup table isn't modified by more than one thread, or that some threads don't re-do work they shouldn't? Are there tradeoffs here that you can think of? 

You'll want to find a good way to get timings. What class or API will give you fine-grained timings?

Think of this as a lab experiment, like in a chemistry or physics class. How will you collect your meausrements? Will your measurements have errors or uncertainty? How will you record that information? Should you run multiple trials? Will your results be comparable to other people who work this exercise?

Also, maybe 1 through 1 million is too large (or too small!) for your computer. Feel free to adjust the range so that it's reasonable (and fun!) for you and your machine.
	