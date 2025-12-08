# Long Block Times

- Date: 2025-DEC-5
- Authors: Hypha
- Status: Cosmos Hub is running normally
- Summary: The Hub has experienced three periods of block time degradation and validator downtime: Nov 26, Nov 27, and Dec 4.
- Impact: Slower block times and failed transactions.
- Root Causes: Multi-send transactions overloaded block processing in the validator nodes.
- Trigger: Multiple multi-send transactions being sent to the network.
- Resolution: Multi-send transactions stopped being sent to the Hub and the mempool cleared eventually. Missing validators started signing blocks after they caught up with the rest of the network.
- Detection: Hypha received alerts for validator downtime, high transaction failure rate, and chain slowdown.

# Action Items

- [Hypha] Investigate increasing the block window parameter in the feemarket module.
- [Hypha] Discuss solution and mitigation options at the Cosmos SDK level with Cosmos Labs team.

# Lessons Learned

## What went well

- Monitoring and alert system worked as expected.
- Comms support documentation worked well: announcements were sent through the Hypha team account in Discord.

## Where we got lucky

- Two spam events lasted less than one hour, and one event lasted less than two hours.
- This is a network slowdown mechanism we have seen before.

# Timeline

## Nov 26

| Time (UTC) | Event                                                                                               |
| ---------- | --------------------------------------------------------------------------------------------------- |
| 22:11      | First block with multi-send transaction is committed                                                |
| 22:13      | Hypha receives alert for validator downtime                                                         |
| 22:21      | Hypha receives alert for high transaction failure rate                                              |
| 22:23      | Hypha notifies Cosmos Labs                                                                          |
| 22:25      | Hypha confirms it is multisend spam                                                                 |
| 22:25      | Hypha receives alert for chain slowdown                                                             |
| 22:33      | Last block with multi-send transaction is committed                                                 |
| 22:40      | CryptoCrew notifies Hypha that other chains are being spammed as well                               |
| 22:47      | High transaction failure rate alert is resolved                                                     |
| 22:53      | Validator downtime alert is resolved                                                                |
| 23:00      | Chain slowdown alert is resolved                                                                    |
| 23:29      | Hypha posts incident update notification in Discord confirming multi-send transactions as the cause |

## Nov 27

| Time (UTC) | Event                                                  |
| ---------- | ------------------------------------------------------ |
| 09:09      | First block with multi-send transaction is committed   |
| 09:14      | Hypha receives alert for high transaction failure rate |
| 09:16      | Hypha receives alert for validator downtime            |
| 09:24      | Last block with multi-send transaction is committed    |
| 09:31      | Hypha notifies Cosmos Labs                             |
| 09:39      | High transaction failure rate alert is resolved        |
| 09:39      | Validator downtime alert is resolved                   |

## Dec 4

| Time (UTC) | Event                                                  |
| ---------- | ------------------------------------------------------ |
| 19:12      | First block with multi-send transaction is committed   |
| 19:40      | Hypha receives alert for high transaction failure rate |
| 20:07      | Hypha receives alert for validator downtime            |
| 21:02      | Validator downtime alert is resolved                   |
| 21:19      | Last block with multi-send transaction is committed    |
| 21:29      | High transaction failure rate alert is resolved        |

# Supporting information

- Sender account: `cosmos1lgars47nzhfzt0mqsjrdzrx2zcg7c2skxcayt2`

|                         | November 26 | November 27 | December 4 |
| ----------------------- | :---------: | :---------: | :--------: |
| Duration+               |     22m     |     15m     |    2h7m    |
| Gas fees paid by sender |   30 ATOM   |   17 ATOM   |  128 ATOM  |
| Longest block time      |     23s     |     17s     |    10s     |
| Minimum voting power    |    66.79    |    66.76    |    67.5    |
| Missed signatures       |    6835     |    3684     |   13747    |

\+ The duration is the time between the first and last blocks that include a `multi-send` transaction from the listed sender account.
