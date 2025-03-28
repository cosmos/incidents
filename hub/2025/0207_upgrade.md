# v22.0.1 patch upgrade

- Date: 2025-Feb-07
- Authors: Hypha and Interchain Labs
- Status: Chain is moving but not upgraded
- Summary: We missed that a patch was marked as ‘consensus breaking’, did not run the necessary tests to catch the error, and published a release for asynchronous upgrades which caused consensus breaks. 
- Impact: 23 validators experienced apphashes and had to restore from a snapshot to start signing blocks again
- Root Causes: Haste, poor communication
- Trigger: Validators upgrading to v22.0.1
- Resolution: Coordinated upgrade is scheduled for Wednesday, assuming a fresh set of upgrade tests pass
- Detection: Validators informed team of apphashes, team investigated and found the release notes marking the wasmvm patch as consensus breaking

## Action Items

- Hypha will run the full suite of tests for every upgrade (including for things that aren’t changing) - each run is a couple hours
- ICL check how to optimize interchaintest upgrade tests
- ICL to subscribe to security alerts
- ICL to build 22.0.3
- Hypha to coordinate 9-10 am for Wednesday Feb 12
  - 22.1.0 will contain comet and wasmvm patches
- ICL to produce a guideline for when to upgrade same day vs wait

## Lessons Learned

- 👍 What went well: 
  - Quick response to validator issues and clear plan of reverting to v22.0.0 and waiting for a retro and further coordination
- 👎 What went wrong: 
  - ICL didn’t catch that the wasmvm patch said it was consensus breaking
  - Hypha wasn’t aware of the wasmvm patch, didn’t test wasmvm code and so also didn’t notice it
  - Non-coordinated upgrade - won’t do that again unless super high security risk
- Where we got lucky: 
  - Validators online at the right time, reporting issues, responsive to instructions
  - That we were online to herd validators
  - Easy path to recovery - snapshots available
- Misc lessons learned
  - How does ICL stay aware of security issues that will impact Hub? - hub-specific security email
  - Deleted the v22.0.1 release so no one could run it. Is this good practice? What should be done instead?
    - Leave this one deleted
    - In the future, revoke it and brick the release
  - How do we make the call on when to upgrade?

## Timeline
- Feb 7 1506 UTC: Hypha and ICL agree that it’s appropriate to release a patch to address CWE-345, aiming for a non-breaking release to occur same day. If the patch is breaking, aim for next week.
- 1936 UTC: v22.0.1 is released, containing version bumps for CometBFT and WasmVM. ICL informs Hypha in Slack.
  - Comet bump 0.38.15 to 0.38.17 to address CWE-345
  - Wasmvm bump v2.1.4 to v2.1.5 to address CWA-2025-001 and CWA-2025-002.
- 1947 UTC: Hypha reports fresh state swap test passes.
- 2036 UTC: Hypha reports sync upgrade with ICS validator on provider testnet passes.
- 2247 UTC: Hypha reports previously failing interchaintest tests pass.
- 2249 UTC: ICL marks v22.01 as latest and moves to post in Discord.
- 2256 UTC: Hypha takes over comms responsibilities due to Discord permissions issues.
- 2309 UTC: Hypha tells validators to apply the non-breaking  v22.0.1 upgrade ASAP, asking validators to emoji react when upgraded.
- Feb 8 0117 UTC: First validator reports an apphash on 22.0.01 (BlockHunters)
- 0133 UTC: Hypha instructs apphashing validators to revert to 22.0.0 and await further instructions on Monday.
- 0157 UTC: iqlusion identifies the relevant block 24318855 
- 0159 UTC: Blockhunters releases a snapshot for validators needing to resync.
- 0308 UTC: Most validators are signing again. Hypha messages all validators who are still missing blocks to check in and communicate next steps.
- 0334 UTC: ICL notices that the wasmvm patch is state breaking and deletes v22.0.1 release.
- 0354 UTC: ICL and Hypha agree to publish a release containing only the non-breaking Comet patch to have on standby in case anyone executes the CWE-345 attack over the weekend. Hypha (Lexa) grants Discord announcement permissions to ICL.
- 0420 UTC: ICL releases v22.0.2 containing only the Comet bump.
- 1447 UTC: Hypha confirms that all validators appear to be signing again and thanks validators in Discord.
- Feb 9 1924 UTC: Ztake validator reports apphash even after rolling back to v22.0.0 with a resync from snapshot.
- Feb 10 1541 UTC: Hypha commits to releasing instructions to validators by 2200 UTC today with 24h notice if a coordinated upgrade is needed.

## Supporting information

Comet security advisory: [CWE-345](https://github.com/advisories/GHSA-r3r4-g7hq-pq4f)
CometBFT: [v0.38.17](https://github.com/cometbft/cometbft/releases/tag/v0.38.17)
Wasmvm security advisories: [CWA-2025-001](https://github.com/CosmWasm/advisories/blob/main/CWAs/CWA-2025-001.md) and [CWA-2025-002](https://github.com/CosmWasm/advisories/blob/main/CWAs/CWA-2025-002.md)
Wasmvm: [v2.1.5](https://github.com/CosmWasm/wasmvm/releases/tag/v2.1.5)
Gaia: [v22.0.1](https://github.com/cosmos/gaia/releases/tag/v22.0.1) and [v22.0.2](https://github.com/cosmos/gaia/releases/tag/v22.0.2)
Neutron coordinated upgrade: planned for [Wed Feb 12, ~11:30 UTC](https://www.mintscan.io/neutron/block/19947000)
