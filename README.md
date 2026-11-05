# Kazah

**Software engineering · JavaScript · Automation**

Building Bitburner systems in public. We share the implementation, the reasoning behind it, and the results as the project evolves.

## Bitburner engineering log

Our focus is turning a growing network into a reliable automation system. Development starts with a working baseline, then improves resource allocation, target selection and execution efficiency through measured changes.

### Verified baseline · November 5, 2026

- Distributed the starter worker across seven servers with 37 execution threads.
- Established a continuous `weaken → grow → hack` cycle against `n00dles`.
- Acquired TOR and `BruteSSH.exe` to unlock SSH ports.
- Gained root access to `CSEC`, installed its backdoor and joined CyberSec.
- Started faction hacking contracts to build reputation alongside script income.

These are recorded milestones. The live save continues to evolve.

### Current worker

The initial worker uses security and money thresholds to decide its next operation. Its target is fixed to `n00dles`, and each deployment runs independently.

```javascript
/** @param {NS} ns */
export async function main(ns) {
  const target = "n00dles";
  const minSecurity = ns.getServerMinSecurityLevel(target);
  const maxMoney = ns.getServerMaxMoney(target);

  while (true) {
    if (ns.getServerSecurityLevel(target) > minSecurity + 3) {
      await ns.weaken(target);
    } else if (ns.getServerMoneyAvailable(target) < maxMoney * 0.75) {
      await ns.grow(target);
    } else {
      await ns.hack(target);
    }
  }
}
```

### Next engineering work

- Automate discovery and deployment using available RAM.
- Compare target profitability using income, execution time and security.
- Coordinate workers to reduce redundant operations.
- Record reproducible performance measurements before and after each change.

### What we share

Working scripts, architecture decisions, deployment steps, progress milestones and experiment results. Each update will distinguish completed work from planned changes and explain the trade-offs behind the implementation.

**Follow the repository history for the evolution of this project.**
