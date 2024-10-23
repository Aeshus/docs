
# Resource-Oriented AI

| Designers | Implemented | GitHub Links |
|---|---|---|
| Aeshus | :warning: Partially? | TBD |

## Overview

old doc: []()

> [!NOTE]
> This proposal is based in part on [Moony's AI proposal]().
> Inspired by [Saphire's proposal](https://docs.google.com/document/d/1h0Vz_3WcmAZuEuARnvdCJNr1yQFqUhJZQOqK5XRNDc4/edit)

The AI is the same "big brother" that can quickly observe any place on the station (that has cameras), which can communicate with crew and interact with technology.

It is a fully digital entity, meaning that it can be easily moved (or de-facto killed) using things like [Intellicards](), and only really interacts with crew through [technology]() and the [radio/holopads]().

In order to balance their frankly obscene amounts of power, this PR introduces the notion of ["Compute" or "Processing Power"]() in order to sustain or extend its capabilities. The idea is that by capping the amount of Compute an AI player has, we force them to make choices on their playstyle. Things like bolting doors, turning APCs off, electrifying doors, etc. would require a constant spend of compute in order to maintain their state, and if too much compute is used compared to the gain, all of the ai's capabilities would be disabled until they cut down or gain more compute.

The AI gains Compute in three primary ways: expanding server infrastructure, 2: upgrading the AI core, and 3: degreading crew-oriented technology. 
- [Server infrastructure]() is anything in the game that's a server, which is currently the Telecomms and Camera routers. 
- [Upgrading the AI core]() comes in the form of sacrificing other silicon beings to it. 
- [Degrading crew-oriented technology]() means that it can disable things like consoles for compute (but it can be reversed by cutting the AI management wire).

For the antagonist ["Malf" AI](), this PR mainly curbs their ability to quickly bolt & electrify the whole station without recourse, while still giving them a path to quickly do similar but more targetted attacks. All of their paths to gaining resources are not explicitly suspicious in any way, and the crew can quickly subvert their expansion by cutting off the antagonist AI's compute sources, requiring them to reduce their attacks.

> [!NOTE]
> 
> We need to think of a way for borgs to be able to strengthen an antagonist AI.

> [!CAUTION]
> 
> This document wasn't directly designed with multiple AIs in mind. They should be possible by sharing the amount of compute between the two AIs, and as such, should probably be implemented in such a way that it is possible for there to be multiple.
> This also allows for a minor "virus" ghost role/antag which wastes compute and needs to be removed from the AI core.

## Background

AI is a staple role for any Space Station implementation. Many different implementations use it for different niches, but this proposal is meant to outline a version that is much closer to an actual role than a glorified observer.

The current implementation in SS14 suffers from two major sins: the AI can do *too* much, and the AI isn't really connected to the crew.

For the abundance of stuff it can do, just look at two common complaints: 
- Antagonist AI ("Malf" or Antimov) is too quickly able to disable the whole space station with no recourse or way of fighting back except changing their laws at the console. They have nothing stopping them from bolting, electrifying, and then cutting power to the whole station. 
- The crew-oriented Validhunting AI is too quickly able to antag hunt around the station, bolting off escape routes and electrifying doors. While I do personally like this playstyle a bit, this PR mainly requires them to focus on things instead of just wandering constantly.

For the lack of crew connection, just look at how:
- There's no real departmental connection to AI. There is basically no reason for the average crew member to ever go to the AI core or ever interact except for command. This pr introduces reasons for crew to see the AI, such as upgrading it.

## Compute

The AI is designed around the central conflict of managing it's compute.

Compute is used for essentially every interaction the AI does, and as such, the AI must make sure to use their compute for the right reasons to ensure that it has enough to continue to function.

The AI would start with a default amount of compute at the start of the shift that it can use for basic functionality (such as connecting to camera routers, to telecomms servers). This default is provided by the starting server infrastructure and by the AI core's default compute gain.

Compute would act like a resource in the way that there it can build up a reserve to spend. When that reserve runs out, all of its continous actions would be disabled.

### Sources

#### Server Infrastructure

Most of the AI's starting compute comes from the station's server infrastructure. Server infrastructure is things like the Telecomms Servers and Camera Routers. They will require power to function properly.

This should give at least enough power for the AI to listen on all radio frequencies and all camera routers.

For a non-antagonist AI, the benifits are:
- It gives them a simple source of compute.
- Incentivizes crew into actually setting up, maintaining, and securing their critical infrastructure.

For an antagonistic AI, the benifits are:
- It makes crew question the need for this critical infrastructure. If the crew really needs to stop the AI, they can cut telcomms and cameras off. 
- It gives another location that the AI desperately needs to defend from crew incursions.
- It heavily incentivizes the AI to not just cut telecomms power, as they are hurting themselves more than the crew by doing that.

For mappers, the telecomms rooms should stay where they are, though camera routers should be placed within their respective departments. If the department doesn't want the AI to see their cameras, they can cut off the AI's access and starve it of compute.

#### AI Core Upgrades

This is another default source of power, which can never go away except being manually removed, and requires specific crew interaction in order to increase.

These AI core upgrades come in the form of silicon life forms being consumed by the core. These would be the Potato pAI, pAI, and Positronic Brains. If a soul was inhabiting that silicon, they would die and the AI would steal their computing power.

There would also be some silicon brains that require research to unlock, which would increase collaboration with science.

> Should the AI be able to hold multiple upgrades (prefered) or only one?

This provides a valid reason for crew to be invited into the AI core (mainly scientists) for the purpose of upgrading the AI. They can then abuse this to emag/antimov the AI. 

#### Degredation of Crew-Oriented Technology

The final source (and greatest potential) is the degredation of crew-oriented technology. This could be things like consoles, machines, lights, etc.

When the AI is degrading it, the crew is unable to use it.

The purpose of this is to provide a viable way for the AI to quickly gain a burst of compute while also making it come at the cost of annoying crew and raising suspicion.

For the non-antagonist AI:
- It provides them additional compte for consoles that the crew just aren't using, such as the power console in the bridge.
- During Nukie shifts, the AI can justifiably use it to force its compute up and defend themselves and the crew.

For the antagonistic AI:
- It lets them quickly gain compute and cause disruption to the station. 
- The crew can simply cut the AI control wire to renable functionality.

### Sinks

There are going to be two types of sinks here: one-time and continous. For things like Cameras and Radio, it makes sense to have them be continous sinks as they are constantly being used by the AI. For things like opening doors or using a console, however, that is a one-time cost.

#### Radio

Radio gives some needed justifications:
- A "silent" AI may just not be using their compute for radio.
- A basically essential sink that will always lower the AI's total compute.
- Incentivizes the malf to stop eavesdropping on crew as they need to spend more compute to defend themselves.

In order to access specific radio frequencies (except binary), the AI will need to spend continous compute.

In order to speak, it uses one-time compute. This incentivizes the AI to use things like its console more and to not simply act as a radio liason between frequencies.

An antagonistic AI could spend one-time compute to impersonate a crew member (like a voice mask) in order to confuse radio communications.

#### Cameras

Cameras are probably the most important thing to an AI player, and as such, will be one of their main draws for compute.

It will need to spend a continous amount of power to connect to specific camera consoles in order to view the cameras attached to it.

There will also be a "general" camera router that will connect to any camera placed on the station that isn't associated with another camera router already.

This forces the AI to choose which camera networks it would like to view, incentivizing them to do things like disabling it's own cameras inside of its core to save compute.

There will also be another continous cost which would let the AI indentify crew members in the camera, which could be toggled on and off at will. This would incentivize the AI to not just look everywhere for crew without IDs.

There'll also be a continous cost to view the health of crew just like the identification ability.

For a non-antagonist AI:
- Incentivizes them to either watch everything and not have much they can do or view little and do a lot.
- Still incentivizes crew to set up cameras and for crew to use the camera router.

For an antagonist AI:
- Incentivizes them to minimize what they're viewing in order to save compute for messing with crew.

#### Doors

Doors are currently the main way that an AI would interact with a station.

Opening doors would be a one-time compute cost as it just opens the door. It's meant to be cheap as it's the main thing a non-antagonist AI would be doing.

Bolting doors would be continous compute as it's activly blocking out a crew member. This is done as to stop an antagonist AI from just bolting the whole station and a metagaming AI from just bolting all the doors to its core.

Electrifying doors would be a higher continous compute as it's activly harming crew. Laws should already restrict most use of it, and as it's a higher cost, it stops the antagonist AI from just electrifying every door like they would currently.

For non-antagonist AI:
- They don't have infinite ability to bolt doors to stop antagonists.

For antagonist AI:
- They now have to selectivly bolt/electrify doors.

#### Consoles

???

1. Crew Monitor (continous while viewing)
2. Communications console (one-time per cost)
3. Criminal Console
4. Research Console

#### Holopads

Holopads are a new way of directly communicating between crew (and the AI). 

It's a one-time cost for the AI.

#### Built-in Abilities

> [!NOTE]
> I'm debating whether these should be available on an "unlock" basis.
> It would give AI some power scaling on their own without upgrades and would temporarily decrease the surplus of compute they have.

#### Turrets

Turrets can be toggled on and off. They shoot all crew! Laws will hopefully stop them from abusing it.

#### Silicons

One-time compute to hack borg and set its laws to the AI's laws.

## Intellicards

Intellicards are the way that the AI can be moved.

## Laws

Something something AI laws?

## Silicons

