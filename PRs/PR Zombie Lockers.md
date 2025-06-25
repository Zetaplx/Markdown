
### Related Issues
Fixes: #38529
## Overview
Exempts humanoid zombies from the check to ensure someone moving out of lockers has hands.
## Reasoning
If for whatever reason you are stuck in a locker, locked or unlocked, when you zombify, you will be stuck there. Zombies, while not possessing hand slots, do infact have hands and should, in my opinion, be able to exit an unlocked locker on their own occord.  
I'd almost be willing to call this a bugfix, but I'll leave it as a tweak unless someone else disagrees.
## Implementation Details
By additing additional components to the abort check at the start of the `OnRelayMovement()` method inside of [`SharedEntityStorageSystem.cs`](https://github.com/Zetaplx/space-station-14/blob/master/Content.Shared/Storage/EntitySystems/SharedEntityStorageSystem.cs), we can allow entities to bypass this check if they possess certain components. In our case, the `ZombieComponent` and `HumanoidAppearanceComponent`.
### Technical  Changes
 – Added requirement that an entity not have both the `ZombieComponent` and `HumanoidAppearanceComponent` in order to bypass `OnRelayMovement()`
### Test Cases
 – [ ] Humanoid Zombies can move out of closed, unlocked lockers  
 – [ ] Humanoid Zombies can resist closed and locked lockers  
 – [ ] Non-humanoid Zombies cannot move out of closed, unlocked lockers  
 – [ ] Non-humanoid Zombies cannot resist closed and locked lockers  
## Media
No current media, will add later.
## Requirements
 – ✅ I have read and am following the [Pull Request and Changelog Guidelines](https://docs.spacestation14.com/en/general-development/codebase-info/pull-request-guidelines.html).  
 – ✅ I have added media to this PR or it does not require an ingame showcase.  
## Change Log
:cl: Zetaplx
- tweak: Zombies can now exit closed lockers by moving.
