[DRG Analysis](README.md) > **LOK-1 Smart Rifle**

# LOK-1 Smart Rifle

## About the gun

The LOK-1 Smart Rifle is a powerful primary (if you take the right builds) that gives up the reactiveness of stubby in exchange for range, armor break, and higher potential DPS if you(r team can help) activate the powerful T3A upgrade. 

SMRT Trigger OS is an overclock introduced in Season 5 that allows you to gain back most of that reactiveness, but in exchange you give up the opportunity to run Executioner whose massive weakpoint bonus helped make up for the weapon's tight base ammo pool. Still, a lot of the general public has been sleeping on SMRT Trigger OS. It kills single targets extremely quickly, at a rate competitive with or exceeding Executioner, which was the previous reigning champion among single-target LOK-1 builds.

The upgrade tree of the weapon is in a rather sad state. Most tiers have preferred or strongly preferred options with a few specific edge cases.
* In Tier 1: 
  * Damage vs ammo, neither option leaves you with much total ammo so you might as well take damage and get better DPS. Ammo does give slightly more total damage but it's still not ideal. I suppose you can take it if you want. I will analyze the builds assuming you take damage, except for the standard ECR build which is not focused on single targets and takes ammo.
* In Tier 2: 
  * T2A (tight lock-on field, long range) is generally considered the best in that tier as it allows you to precisely specify which target you want to place locks on - obviously a useful capability for a single-target weapon. It also gives you a huge range. It is even useful for ECR to concentrate three locks onto a single target in order to activate the overclock's signature explosion - with a wider lock-on field, the locks tend to get scattered over multiple targets which can waste both time and ammo.
* In Tier 3:
  * T3A (electric/fire synergy) is up to a 40% damage upgrade if you can apply statuses (and is additive with T5B for up to 60% extra damage). The extra damage is dealt as Electric or Fire, which means it is even more effective against many enemies such as Mactera. 
  * T3B (SMRT targeting) is sadly a throw pick for single target applications, making it often impossible to get T5B (damage bonus at full lock) and also not accounting for a million factors such as armor which may mean it actively *prevents you from killing enemies*. It also makes it impossible to activate ECR on swarmers if you're going for AOE. 
  * T3C (blowthrough) is not a great pick for single target applications because blowthrough doesn't work until after the bullet hits your locked target, and it's not a great pick for AOE because it's glitchy and causes ECR to straight up fail to activate.
* In Tier 4:
  * T4A (faster locks) is very good, increasing your effective rate of fire. 
  * T4B (more locks) is only marginally useful while making it harder to activate T5B (damage bonus at full lock). Exception for SMRT Trigger OS since it makes your lock-ons instant anyway, therefore just being a rough x2 rate of fire multiplier.
* In Tier 5:
  * T5A (electric DOT) is very good and can activate T3A (electric/fire synergy) on subsequent shots.
  * T5B (damage bonus at full lock) is also very good, and the choice between it and T5A mostly comes down to whether you expect to have a plentiful other source of electricity.
  * T5C (fear) barely applies enough fear to do anything and is competing with significant damage/utility upgrades. Oof

## My complaints

There are quite a lot of fiddly details that become annoying when trying to calculate the DPS of this gun.
* There is a complicated sequence of events that happens each time you fire a burst:
  * A 0.25s delay before locks begin to be acquired
  * Locks are gradually placed on the target
  * The gun waits for you to manually let go of the trigger, which you are almost certain to do a bit late (thus losing DPS) or a bit early (thus getting less than full locks and losing T5B)
  * The gun fires the locked shots in a burst
  * There is a 0.2s delay before the start of the next cycle (or the start of the reload) due to the gun's actual rate of fire of 5 (which is the rof at which you can tapfire)
  * Finally, SMRT Trigger throws most of this out the window, letting you hold down the button and locking on much faster and ditching the 0.2s rate of fire delay and having an extremely high burst rate of fire. There are additional anomalies with it that cause it to just not match any kind of calculation I could put together. Therefore, SMRT Trigger is best analyzed by just recording the game and timing the recordings. Which leads us to the next issue.
* The following things do not change simultaneously and tend to be offset by a few frames from each other. The best approach is to pick one of these and use that one only:
  * The lock icon on the target
  * The lock bar on the left of the crosshair
  * The magazine counter on the weapon model
  * The magazine counter on the HUD
  * The health bar of the target
  * The visual firing animation of the weapon (which we could further dissect into multiple components but I'll spare you the details)
* T3A can get bonuses or not depending on what status effects the target has.
* T5A electric upgrade adds an additional electric DOT which can affect T3A.
* Normal fiddly DRG details like punching through armor and hitting weakpoints and blowthrough weirdness and reload cancelling and etc etc etc.

## General build comparison

OK so how to analyze this weapon? For the graph below, I'll make some simplifying assumptions:
* You play perfectly and let go of the trigger immediately when the gun reaches max locks (except SMRT Trigger OS where you just keep holding the trigger and perfect play is actually humanly possible)
* T3A and T5B are always active to their full extent (though the fire/electric DOT that activate them won't be counted into the damage, only the T3A bonus)
* Reasonable reload cancels are performed according to [LazyMaybe's timings](https://www.youtube.com/watch?v=TQ0-ysX-ZX4).

![](img/lok1.png)

This graph assumes you start holding the trigger at time 0. The last horizontal segment in each curve is a reload (with reload cancel). For slow-locking builds, the reload takes about as long as filling up the lock bar. 

SMRT Trigger and Executioner are clearly the most reactive and have the highest DPS. It is pretty clear why the two of them are considered so much stronger than the base weapon. ECR is also considered strong, but obviously not as a single-target weapon, being more useful for its explosion which inflicts some AOE and fear. (Ideally you want to use bursts of 3 locks to spam explosions rather than full lock, but the 3-lock version of the graph went way off the right edge so I decided to just not show it. You can still full lock if you want to deal with a single target.) Seeker has the next lowest DPS, with less than half the burst of Executioner (though slightly more than half if you include the reload time.) 

## Exec cases and SMRT Trigger OS

Since SMRT and Exec are our top contenders, let's look at them in a little more detail. This time, I have specifically noted which bonuses apply. T5A electric dot is included. I have also added a 0.2s delay during each Exec firing cycle to account for imperfect play. 

I have also added breakpoints (Haz6p4), though not accounting for enemy resistances/vulnerabilities to electricity or fire. Enemies with breakable heavy armor (Brundles, Stingtails) tend not to punch through until the second hit, so I have added one bullet's worth to their effective health.

Under these assumptions, SMRT now consistently kills faster than Exec even when Exec is hitting weakpoints. (The exception is when 11112 Exec gets T3A and SMRT doesn't, which isn't a fair comparison. I added that Exec case more as a comparison against the other Exec cases.) When Exec isn't hitting weakpoints, it falls way behind. There are a few quite notable enemies where this is relevant, especially shellbacks. You can't one-mag a rolling Haz6p4 shellback with Exec unless you take 11112 and the shellback is on fire (rolling shellbacks are completely immune to electricity, and you aren't likely to hit a weakpoint). 

The tradeoff for this DPS and reactiveness is that as I mentioned at the beginning, SMRT Trigger OS doesn't get many massive bonuses to increase its total damage pool. So you'll have to pick your targets and be mindful of your pacing, especially in teams where resupplies are less plentiful. Still, it's way better than the base weapon and I think it deserves to have a reputation equal to Executioner's.

![](img/lok1_exec.png)

[Back to DRG Analysis](README.md)