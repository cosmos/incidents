# Action Items from 2025 Retrospectives

This document summarizes all action items from the retrospectives in the `hub/2025` folder.

## Preventive Action Items

These action items focus on preventing future incidents through improved testing, build processes, and system architecture changes. They aim to catch issues earlier in the development cycle.

| Action Item | Source | Owner | Notes |
|-------------|--------|-------|-------|
| Adjust feemarket params | [0127_block_times.md](2025/0127_block_times.md) | ICL | Temporary stopgap |
| Create appropriate load tests mimicking the incident | [0127_block_times.md](2025/0127_block_times.md) | Team | Multisend load |
| Run the full suite of tests for every upgrade | [0207_upgrade.md](2025/0207_upgrade.md) | Hypha | Including for things that aren't changing - each run is a couple hours |
| Check how to optimize interchaintest upgrade tests | [0207_upgrade.md](2025/0207_upgrade.md) | ICL | |
| Update blst library via go mod edit -replace | [0326_v23stack.md](2025/0326_v23stack.md) | ICL | Team to push up v23.0.2; Hypha to verify v23.0.2 on provider testnet; May conflict with upcoming security patch |
| Add Werror to fail builds on linker warnings | [0326_v23stack.md](2025/0326_v23stack.md) | ICL | |
| Figure out bump to go 1.24 to update prism | [0326_v23stack.md](2025/0326_v23stack.md) | ICL | |
| Open an issue in the SDK | [0326_v23stack.md](2025/0326_v23stack.md) | ICL | So that every way of halting a node halts on the exact same block |
| Figure out what the constraints are for CPU architectures that can/can't run gaiad | [0326_v23stack.md](2025/0326_v23stack.md) | Team | Hypha to offer points in exchange for info on CPU architectures |
| Update workflows to compile the new binary | [0326_v23stack.md](2025/0326_v23stack.md) | Hypha | Mirroring how most validators operate |
| Investigate sdk-level features to eliminate manual halt-height upgrades | [0414_upgrade.md](2025/0414_upgrade.md) | Hypha | |
| Investigate source of non-deterministic behaviour | [0414_upgrade.md](2025/0414_upgrade.md) | Hypha + ICL | |
| Write and publish informational blog post | [0414_upgrade.md](2025/0414_upgrade.md) | Hypha + ICL | About upgrade styles and improving the Hub upgrade process over time |

## Detective Action Items

These action items aim to improve monitoring and detection capabilities to identify issues before they become critical incidents. Enhanced telemetry and visibility will enable faster diagnosis and response to network anomalies.

| Action Item | Source | Owner | Notes |
|-------------|--------|-------|-------|
| Enable additional telemetry for rechecked transaction failures and peer disconnects | [0127_block_times.md](2025/0127_block_times.md) | Team | Kz: who is monitoring this? |
| Gain additional visibility into the status of the live Hub network | [0127_block_times.md](2025/0127_block_times.md) | Team | Validator profiles, metrics, logs |
| Subscribe to security alerts | [0207_upgrade.md](2025/0207_upgrade.md) | ICL | |

## Response Action Items

These action items focus on improving incident response procedures, automated remediations to stop the bleeding, and coordination between teams. They establish clear guidelines, processes and automations to enable faster, more effective responses when issues occur.

| Action Item | Source | Owner | Notes |
|-------------|--------|-------|-------|
| Produce a guideline for when to upgrade same day vs wait | [0207_upgrade.md](2025/0207_upgrade.md) | ICL | |
| Make proposal to reduce governance voting period parameters | [0414_upgrade.md](2025/0414_upgrade.md) | Hypha | To allow for expedited proposals to coordinate halt height in an emergency |
| Test impact of pruning configuration in rollback command | [0414_upgrade.md](2025/0414_upgrade.md) | Hypha | To reduce rollback time |
| Define a critical emergency process between Interchain Labs <> Hypha | [0414_upgrade.md](2025/0414_upgrade.md) | ICL | From parent retro |
| Adopt Celestia's upgrade mechainism | | Team| |

## Recovery Action Items

These action items focus on improving recoverability of incidents after the initial stop-the-bleeding responses.

| Action Item | Source | Owner | Notes |
|-------------|--------|-------|-------|

