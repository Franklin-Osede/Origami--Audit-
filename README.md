### Origami Protocol Security Audit

Voluntary Security Research & Methodologies for Ori.Network

About the Ori.Network Protocol

Ori.Network provides a universal liquidity layer for cross-chain asset transfers. Through a mint-and-burn mechanism, the protocol enables users to:

Mint wrapped assets by locking underlying tokens in liquidity pools.

Bridge those assets across supported chains.

Burn wrapped assets to redeem the original tokens on any destination chain.

This architecture decouples liquidity from any single blockchain, optimizing for high throughput, low fees, and seamless DeFi composability.

### Repository Overview

This repository contains automation scripts, configuration templates, and documentation of the security research approach applied to the Origami smart contracts. As a volunteer researcher, I focus on exploring attack surfaces rather than delivering formal findings.

### Research Scope & Objectives

My voluntary engagement emphasizes:

Familiarizing with contract flow: entry points, state transitions, and external calls.

Attempting to surface issues related to reentrancy, access control, and edge-case logic.

Stress-testing fee calculations and reserve accounting under atypical input values.

### Contracts under review:

OrigamiBridge.sol

LiquidityPool.sol

Vault.sol

FeeManager.sol

AccessControl.sol

Techniques & Tools Used

To systematically probe the protocol, I employ a combination of automated and manual techniques:

### Static Analysis

Slither: Identifies common Solidity anti-patterns and potential misconfigurations.

Mythril: Scans for executable paths to known exploit categories.

Securify & Oyente: Cross-check findings for consistency.

### Dynamic & Fuzz Testing

Echidna: Property-based fuzzing to explore invariant violations.

Manticore: Symbolic execution to trace complex code paths.

Foundry (forge): Custom test harnesses for edge-case scenarios.

### Formal Verification

Certora Prover: Proofs for critical asset custody invariants.

Manual Review & Penetration Techniques

Code walkthroughs targeting unchecked math, improper access checks, and external-call sequencing.

Transaction simulation with Hardhat to test revert conditions and event emissions.

Custom scripts using Brownie or Web3.py to simulate multi-user interactions.

### Setup & Usage

# Clone repository
git clone https://github.com/Franklin-Osede/Origami--Audit-.git
cd Origami--Audit-

# Install static analysis tools
npm install --save-dev slither-analyzer mythx-cli securify oyente

# Install fuzzing & symbolic tools
npm install --save-dev echidna-core manticore forge

# Lint & format
npm install --save-dev solhint prettier prettier-plugin-solidity

# Run Slither
npx slither contracts/

# Run Echidna fuzz tests
echidna-test contracts/ --config echidna-config.yaml

# Symbolic execution with Manticore
manticore --output-dir reports/manticore contracts/OrigamiBridge.sol

Documentation of Attempts

All tool runs and manual test logs are recorded under /research-logs. Each execution includes:

Tool name & version

Configuration parameters

Date & time of execution

Key observations (e.g., warnings, exceptions, non-standard behavior)

These logs serve as a foundation for further analysis and collaboration.

Current Status

As of the latest review, no vulnerabilities or critical issues have been identified. Research is ongoing, and new tests will be documented in /research-logs as they are conducted.

Collaboration

All tool runs and manual test logs are recorded under /research-logs. Each execution includes:

Tool name & version

Configuration parameters

Date & time of execution

Key observations (e.g., warnings, exceptions, non-standard behavior)

These logs serve as a foundation for further analysis and collaboration.

Collaboration

Fellow researchers are encouraged to:

Fork this repo and add new scripts or test cases.

Open issues describing additional techniques or edge cases.

Submit PRs with improved configurations or sample exploits.

Disclaimer

This work represents voluntary research and does not constitute an official audit. Use these methodologies at your own discretion.
