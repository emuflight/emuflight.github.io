---
layout: default
title: i_decay
parent: Features
nav_order: 6
---

# i_decay
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### What is i_decay?
EmuFlight has a tuning parameter called i_decay. i_decay is a powerful tool for reducing iterm windup and bounceback at the end of quick flips and rolls. Increasing i_decay means that you can run a higher i without many of the negatives associated with a high i.

### How does it work?
i_decay works by taking the iterm windup which is normally accumulated during sharp moves and increases how quickly it shrinks. By increasing your i_decay you are literally increasing how quickly the iterm would naturally decrease after a windup. An i_decay of 1 actually turns off the functionality of the i_decay. An i_decay of 2 make the decrease in the iterm twice as fast while an i_decay of 5 makes the iterm decrease 5 times as fast as it normally would. 

***@Skylion Tip:*** When tuning I_decay I usually start at 5 and do a bunch of fast flips and rolls. You'll want to particularly pay attention the the end of the flips/rolls and how your quad catches itself, if your getting bounce back or other unstable movements then raise it by 1 till you see that go away. I like I_decay set to 7 on micros and 8 on 5"+.

### iDecay v2 (0.3.2+)
adds `i_decay_cutoff` where default is `200` (20.0%) threshold of iterm accumulation before full iDecay strength is applied. When iterm accumulation is below the cutoff value the iDecay strength shrinks linearly until iterm is 0, at which point iDecay has no more effect. This was added as testing showed that iterm was able to create slow wobbles in forward flight and other situations when iDecay was too aggressive. This change allows the quicker shrinking of iterm accumulation while preventing iterm from "bouncing" around 0% accumulation. This change means you may prefer a higher iDecay value then previously. Do you want to change the cutoff? Probably not, from our testing every user was happy with the cutoff at 200 and found that to work quite well, as such that is the default and because this works so well we have no plans to add this into the configurator and will remain a cli only setting. But feel free to play with things!