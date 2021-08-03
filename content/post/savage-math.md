+++
title = "Savage Math"
date = 2021-08-03T11:21:28-04:00
+++


I recently dove into Savage Worlds, and I’m really liking what I’m seeing of the game. One thing that keeps tripping me up, though, is the math.  As a hobbyist game designer, I always tend to look at the odds of success on various rolls, and Savage Worlds math is deceptive.


## The Basics

Take melee, for example. d6 is generally described as being “average” at a skill. (In Savage Worlds, your skill is determined by what die you roll, instead of a static bonus, so d4 is poor, d6 is average, d8 is good, d10 is great, and d12 is masterful). In melee, the number you need to hit with a roll of your fighting die is the other person’s Parry score, which is half their Fighting die size +2. So for someone with a d6, they have a Parry of 5.  That means that two equally skilled, average fighters only hit on a 5+... which is only 33% of the time. Ouch… that’s a lot of whiffing for equally skilled characters.


## Wild Cards

But that’s the deceptive part. You see, Savage Worlds PCs and special NPCs (collectively called “Wild Cards”) also get a Wild Die. This is an extra die, always a d6, which they roll in addition to whatever skill or attribute they’re rolling. You use the higher of the two die rolls and add modifiers afterward. Of course, figuring out that math by hand can be tricky, which is why I just plug the numbers into AnyDice.com, a fantastic resource for figuring out die math. For finding the highest of two rolled d6’s, you plug in `output [highest of 1d6 and 1d6],` click “calculate” and then click “at least” and you get a graph like this:



![screenshot of graph from anydice](static/anydiced6wild.png)


The numbers in parentheses after “output 1” are the average and the standard deviation. But the most interesting part is the numbers next to the graph. They show how likely you are to roll that number or higher (what anydice calls “at least”).  So you have a 55.56% chance to roll at least a 5.


## Exploding Dice

Savage Worlds’ other trick up its sleeve which makes mathing possibilities even harder is exploding dice. Whenever you roll the maximum on a die, you grab another die of the same size, roll it, and add the result to the first die. That second die can explode the same way, and so on. So that d4-2 untrained check can roll a 4, and then roll another 4, and another, subtract 2, for a total of 10 on your d4-2. Kaboom.

To math up the possibilities there, we use AnyDice’s `explode` feature. So, a Wild Card character rolling an untrained skill check would be calculated like this: `output [highest of [explode 1d4]-2 and [explode d6]-2]` (note that the -2 from being unskilled also applies to the wild die’s roll, and in AnyDice, you need to put the -2 outside the exploded section, or the -2 gets applied to each newly rolled die… ask me how I know). 

This gives us a graph that looks like this:


![screenshot of graph from anydice](static/untrainedwild.png)


Technically there’s no upper limit to what you can roll, but AnyDice only calculates 3 explosions, and that’s unlikely enough that it runs into tiny percentages anyway.

So this is an interesting result. The chances of a Wild Card character succeeding on an untrained skill check is almost 1 in 3. That’s not great, but it might be better than you were expecting, since 1d6-2 only gets a 4+ 16.67% of the time.

BUT… if you can get +2 from an edge or other beneficial circumstance, all of a sudden, you’re looking at a 63% chance of success, untrained! That’s pretty good! I mean, it’s ain’t a sure thing, but it happens more often than not.

And that’s what I mean about the math in Savage Worlds being deceptive. You can’t easily do the math in your head for any particular scenario, you have to play a lot and get a feeling for how often various rolls work… or you need some sort of crazy lookup table.  

![image of meme of character looking at screen and then away](static/lookaway.png)

## The Crazy Lookup Table

<table>
  <tr>
   <td>
   </td>
   <td><strong>2+</strong>
   </td>
   <td><strong>3+</strong>
   </td>
   <td><strong>4+</strong>
   </td>
   <td><strong>5+</strong>
   </td>
   <td><strong>6+</strong>
   </td>
   <td><strong>7+</strong>
   </td>
   <td><strong>8+</strong>
   </td>
   <td><strong>9+</strong>
   </td>
   <td><strong>10+</strong>
   </td>
   <td><strong>11+</strong>
   </td>
   <td><strong>12+</strong>
   </td>
   <td><strong>13+</strong>
   </td>
   <td><strong>14+</strong>
   </td>
   <td><strong>15+</strong>
   </td>
   <td><strong>16+</strong>
   </td>
  </tr>
  <tr>
   <td><strong>untrained (d4-2)</strong>
   </td>
   <td>63%
   </td>
   <td>50%
   </td>
   <td>32%
   </td>
   <td>27%
   </td>
   <td>19%
   </td>
   <td>17%
   </td>
   <td>13%
   </td>
   <td>9%
   </td>
   <td>4%
   </td>
   <td>3%
   </td>
   <td>2%
   </td>
   <td>2%
   </td>
   <td>1%
   </td>
   <td>1%
   </td>
   <td>0%
   </td>
  </tr>
  <tr>
   <td><strong>d4</strong>
   </td>
   <td>96%
   </td>
   <td>83%
   </td>
   <td>63%
   </td>
   <td>50%
   </td>
   <td>32%
   </td>
   <td>27%
   </td>
   <td>19%
   </td>
   <td>17%
   </td>
   <td>13%
   </td>
   <td>9%
   </td>
   <td>4%
   </td>
   <td>3%
   </td>
   <td>2%
   </td>
   <td>2%
   </td>
   <td>1%
   </td>
  </tr>
  <tr>
   <td><strong>d6</strong>
   </td>
   <td>97%
   </td>
   <td>89%
   </td>
   <td>75%
   </td>
   <td>56%
   </td>
   <td>-
   </td>
   <td>31%
   </td>
   <td>26%
   </td>
   <td>21%
   </td>
   <td>16%
   </td>
   <td>11%
   </td>
   <td>-
   </td>
   <td>5%
   </td>
   <td>5%
   </td>
   <td>4%
   </td>
   <td>3%
   </td>
  </tr>
  <tr>
   <td><strong>d8</strong>
   </td>
   <td>98%
   </td>
   <td>92%
   </td>
   <td>81%
   </td>
   <td>67%
   </td>
   <td>48%
   </td>
   <td>38%
   </td>
   <td>25%
   </td>
   <td>22%
   </td>
   <td>18%
   </td>
   <td>14%
   </td>
   <td>10%
   </td>
   <td>9%
   </td>
   <td>7%
   </td>
   <td>5%
   </td>
   <td>3%
   </td>
  </tr>
  <tr>
   <td><strong>d10</strong>
   </td>
   <td>98%
   </td>
   <td>93%
   </td>
   <td>85%
   </td>
   <td>73%
   </td>
   <td>58%
   </td>
   <td>50%
   </td>
   <td>40%
   </td>
   <td>29%
   </td>
   <td>18%
   </td>
   <td>15%
   </td>
   <td>12%
   </td>
   <td>11%
   </td>
   <td>9%
   </td>
   <td>8%
   </td>
   <td>6%
   </td>
  </tr>
  <tr>
   <td><strong>d12</strong>
   </td>
   <td>99%
   </td>
   <td>94%
   </td>
   <td>88%
   </td>
   <td>78%
   </td>
   <td>65%
   </td>
   <td>58%
   </td>
   <td>50%
   </td>
   <td>41%
   </td>
   <td>31%
   </td>
   <td>21%
   </td>
   <td>-
   </td>
   <td>11%
   </td>
   <td>10%
   </td>
   <td>9%
   </td>
   <td>8%
   </td>
  </tr>
</table>


Numbers from here: [https://anydice.com/program/23943](https://anydice.com/program/23943) 

These are the chances of rolling the given number or higher, if your main die is what is shown on the left, and you’re also rolling a d6 Wild Die. I rounded to the nearest whole number for legibility, and truncated the table at 16, because really, at that point, you’re already succeeding with wild abandon.

While painstakingly copying the numbers from AnyDice, it took me a moment to notice that a skill of d6 _can’t_ roll a 6 or a 12. d4, d8, and d10 _can_ roll their die size, because the wild die can explode to that amount. And it does explain why there’s always a big dip in the percentage at the given’s die’s size, only the wild die can help get that number.

So, there you go. Now you know that when two Wild Cards with d6 fighting attack each other, they actually have a 56% chance of hitting. That’s not that bad. And in fact, even a d4 fighting has a 50% chance to hit someone with a fighting skill of d6 (and thus a Parry of 5).

One of the impressive things about the exploding dice is just how long the tail is. An average d6 Wild Card still has a 5% chance to roll 13+.

You can definitely see that untrained is fairly bad, but even then you have almost a 1 in 3 chance of success a simple 4+. The lowly d4 has 63% chance of success on a 4+, and the “average” d6 succeeds 75% of the time. That’s really good, actually.

I like high chances for success in an RPG. Failing half the time like some RPGs expect, means you can’t actually count on any of your abilities. They’re just a coin flip. Being “average” and having a 75% chance of success is just about perfect, though, in my opinion. Failure is definitely still quite likely, but it’s somewhat unexpected when it happens. And that’s exactly the way it should be. Failing all the time is not fun. It’s the *chance* of failure that really makes the game interesting.

## Extras

I’ll touch on the percentages for Extras (non-Wild Cards) only briefly, mostly because I don’t feel like typing out another gigantic table. You can see the results for yourself here: 

[https://anydice.com/program/23941](https://anydice.com/program/23941) 

It ain’t great, Dan. Chance of success isn’t *too* hard to do in your head without the Wild Die, but here’s the straight percents for hitting a generic 4+:
```
Untrained	19%
D4		    25%
D6		    50%
D8		    63%
D10		    70%
D12		    75%
```
So, it takes an Extra with a d12 skill to be as good as a regular old d6 Wild Card. Ouch.

## Conclusion

And that’s what all I have for Savage Math right now. Pretty interesting stuff. It’s super interesting how the exploding dice and the wild die really work together to make the math work for PCs (but don’t count on your friendly Extras for much help!)

 
