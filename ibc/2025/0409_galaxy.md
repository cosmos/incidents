# IBC Eureka vulnerabity - Galaxy - 2025-04-09

## What happened?

Asymmetric Research discovered a critical vulnerability in the Ethereum light client we were using on the Cosmos Hub and Lombard. We proceeded with an emergency critical upgrade on the Hub, which gave us the authorization to migrate IBC Wasm light clients.

## Root cause

The Ethereum light client did not correctly verify the sync committee, i.e. did not verify that a pubkey is part of the committee. Additionally, an issue with pubkey verification allowed to use non-existing public keys, allowing to bypass the sync commitee signature check.

The reason we needed an emergency patch on the Hub is because we expected significant volume of tokens between Ethereum and the Hub. We could not migrate the light client itself in the upgrade, which meant that we needed to be given rights to migrate the light client ourselves.

Sync committee size verification was dropped because we had to support two hardforks at the same time and could not do it properly because of deadlines.

## Action items

- Set up security council on the Hub, similar to the one on Ethereum
- Figure out a better critical emergency process between Hub <> ICL <> Hypha
- Continuously validate threat models in external dependencies (for example - using Optimism's failure mode analysis)
- Convert TODOs into potential security risks

## Learnings

- We did not have the same tools used for security on the Hub (e.g. security council) as we did on Ethereum - for emergency upgrades this is a must
- We did not have confidence on the level of security details we should reveal to whom
- We did not have enough knowledge on how BLS aggregation works
- We need to raise risky decisions earlier on (reducing type safety to hit deadlines)
- We shipped security features (rate limits) that we had no concept of a plan for using
- The Cosmos Hub's team should have been involved in the patching process
    - This makes coordinating with external partners (i.e. Hypha) much easier

## Timeline (UTC)

- 2025-04-09 14:43: Issue reported by AR
- 2025-04-09 15:00:	Triage has started by the Security + IBC teams
- 2025-04-09 16:00:	Issue is triaged and verified, war-room has been created
- 2025-04-09 16:07:	Decision to continue launch was made and decision how to upgrade the Cosmos Hub was made
- 2025-04-09 17:00:	Access for all non-critical engineers was cutoff to production systems
- 2025-04-09 18:00:	Hub team was notified about an imminent required emergency upgrade
- 2025-04-09 18:20:	Hypha is notified about the same
- 2025-04-10 9:00:	Fix released by IBC team
- 2025-04-10 10:00:	Fix is reviewed by AR
- 2025-04-10 12:00:	Eureka is launched
- 2025-04-10 21:00:	Lombard is migrated to the new light client
- 2025-04-14 16:40:	Cosmos Hub is beginning the upgrade
- 2025-04-14 19:00:	Cosmos Hub resumed block production
