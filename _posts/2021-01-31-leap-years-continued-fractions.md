---
layout: post
title: Leap years and continued fractions
date: 2021-01-31
---

As a year is not precisely 365 days in length and as it is most favorable for
calendars to preserve years as integer multiples of days, the technique of leap
years balances the offset. The most primitive form of leap years would be to add
a day to every 4th year, resulting in an average year length of 365.25 days,
close enough to the 'real' year for daily calendar purposes and over the span of
anyone's lifetime. However, more elaborate systems have been introduced to
account for a greater accuracy in this regard. In this article, I discuss a
system based the continued fraction expansion of the length of the year, and a
prove a small optimality theorem about it.


# Tropical years, sidereal years, and the Gregorian calendar

The Gregorian calendar uses a 400-year cycle of leap years whereby a leap year
is defined to be a year that is: divisible by 400, or divisible by 4 but not by 100.
For instance, the years 2000, and 2004 are leap years, whilst the year 1900
is not a leap year. This results in a cycle of 400 years of which 100 - 3 = 97
are leap years and an average year length of precisely 365.2425 days, which is
quite close to the intended length of the tropical year, that is, the time it
takes for the sun to appear in the same relative position in the sky once again,
which is 365.2422 according to [one article by
NASA](https://www.grc.nasa.gov/www/k-12/Numbers/Math/Mathematical_Thinking/calendar_calculations.htm)
which also calculates that the Gregorian calendar overshoots by one day about once
every 3,300 years.

The tropical year differs from the sidereal year, i.e. the length of the orbit
of the Earth because of the precession of the Earth's axis over the period of
around 26,000 years. Both are not constant due to perturbations from other
planets and stars and whatnot, and it seems that, at least for the tropical
year, they can change quite a bit! To explain my ideas below, I will take the
number 365.242190402 published by the [Paris
Observatory](https://hpiers.obspm.fr/eop-pc/models/constants.html) as the length
of the tropical year. I will consider it constant and exact for simplicity.

# Leaping and continued fractions

The concept of picking leap years is inherently connected to continued
fractions. Consider the simple Julian rule of the 4th year being a leap year.
The intuition behind it is that the length of the year is 365 and 1 out of 4
years have an extra day. Translated to numbers this corresponds exactly to
saying that the length of the year is 365 + 1/4, that is, 365 and 1 for every 4.

**Note: JavaScript needed for some LaTeX display in the rest of the document**

In general, for a common year of length $$n$$ where every $$m^\text{th}$$ year
is a leap year, the actual length of the year is naturally described as $$n +
\frac 1 m$$, the basic pattern which repeats recursively in continued fractions.
You can say that the form $$n + \frac 1 m$$ is a _leapy_ form.

# Recursive leaping
The continued fraction for the length $$l = 365.242190402$$ of the tropical year
is $$[365, 4, 7, 1, 3, 20, 1, 3, 2]$$, otherwise written as:

<center>
    $$ l = 365 + \frac 1 {4 + \frac 1 {7 + \frac 1 {3 + \frac 1 {20 + 
    \frac 1 {1 + \frac 1 {3 + \frac 1 2}}}}}}$$
</center>

The interpretation of $$365 + \frac 1 4$$ being "365 days and one out of 4 years
being leap" is now clear; however, the question arises with the interpretation
of the remaining terms. They key here is the recursive nature of continued
fractions.

To consider the continued fraction up to the third term and then translate
naively as above would give "365 days and one out of $$4 + \frac 1 7$$ years
being leap". The leapy form $$4 + \frac 1 7$$ will correspond to something where
we have the sentence "4 $$X$$ and one out of 7 $$Y$$ being leap". Where  $$4X$$
is the length is the length of a common $$Y$$, so that  $$5X$$ is the length of
a leap $$Y$$. $$X$$ here is a year since every 4-years make a cycle, but what
then is $$Y$$? We can think of $$Y$$ as a "block" of years.

In this analogy, a leap block would mean that it is 5 years long. In other
words, for every 6 passings or the 4-year cycle, the 7th passing is a 5-year
cycle, so you count "1, 2, 3, 4 is leap" 6 times and "1, 2, 3, 4, 5 is leap"
once, and repeat for a cycle of length 29 years.

Here, years replaced days, and blocks replaced years. To interpret the next term
3, we do the same with blocks of blocks. In general, we can define days and
years to be blocks too and fit them into a hierarchy $$b_0, b_1, b_2, \cdots$$.
Here $$b_0$$ corresponds to days, so that $$b_1$$ corresponds to "blocks of days", i.e.
years, and so on and so forth.

# Benefits
The benefits of this system consist of 3 major points. 

1. Whenever the constants change and/or more accurate measurements are found,
   the way to adjust is unambiguous, automatic, immediate, and standard.
2. The system achieves the shortest possible cycle for a given accuracy. This
   result is provable because the convergents of a continued fraction are those
   fractions where the denominator is the least possible for the given accuracy.
3. The approximations are gradual and thus respect locality, meaning that on the
   smaller-scale, the adjustments look like the best approximations for that
   scale, and as the scale grows this is still respected, so the system is
   stable on the scale of thousands of years as well as the scale of 4 years, or
   29 years, etc...

# Issues

A friend of mine<sup>[CAD](#CAD)</sup> made a notable remark about the matter
that the system is very complicated that it could not reasonably be a good idea
if one is manually tracking leap years. I had thought of using this system
completely automatically within clocks in digital devices such as phones and
whatnot; however, he noted that the automation of such things would lead to
people being oblivious to how time is managed, and that the spread of similar
"we will handle it for you" situations to things as basic and date and time
would be a dangerous situation with respect to the freedom of the general
population.

<a id="CAD" href="https://charbelabidaher.xyz">CAD -- Charbel Abi Daher, charbelabidaher.xyz</a>
