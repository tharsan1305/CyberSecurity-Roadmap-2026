# Day 27 - Zero Trust Architecture

## Goal
Understand the modern security model replacing traditional "trusted network perimeter" thinking - increasingly the standard architecture expected in enterprise and cloud security roles.

---

## 1. "Never Trust, Always Verify" Principle

Traditional security model: anything inside the network perimeter (behind the firewall) was implicitly trusted - a "castle and moat" approach.

Zero Trust model: **no user, device, or system is trusted by default**, regardless of whether it's inside or outside the network. Every access request must be verified.

Core idea: assume breach - design systems as if an attacker may already be inside the network, minimizing what they can reach even if they get in.

## 2. Micro-segmentation

Instead of one flat internal network where, once inside, an attacker can move freely (lateral movement), Zero Trust breaks the network into small, isolated segments.

Each segment has its own access controls, so compromising one segment doesn't automatically grant access to others.

Example: a compromised HR workstation should NOT have network access to the finance database server, even though both are "inside" the corporate network.

## 3. Identity-based Access Control

Access decisions are based on **identity and context**, not network location.

Factors considered:
- Who is the user? (authenticated identity)
- What device are they using? (device health/compliance)
- What are they trying to access?
- What's the context? (location, time, behavior pattern)

This ties closely to IAM concepts (covered in the Cloud phase, Topics 36-37) - Zero Trust relies heavily on strong identity and access management.

## 4. Continuous Verification

Unlike traditional models where authentication happens once at login, Zero Trust continuously re-evaluates trust throughout a session.

Examples:
- Re-authentication triggers (sensitive action attempted, anomalous behavior detected)
- Continuous device posture checks (is the device still compliant/patched?)
- Session risk scoring that can revoke access mid-session if risk increases

---

## Interview Questions

**Q1. What does "Zero Trust" mean?**
A security model where no user or device is trusted by default, regardless of network location - every access request is verified based on identity and context.

**Q2. How does Zero Trust differ from traditional perimeter security?**
Traditional security trusts anything inside the network perimeter; Zero Trust assumes breach and verifies every request continuously, regardless of location.

**Q3. What is micro-segmentation?**
Dividing a network into small, isolated segments with independent access controls, limiting lateral movement if one segment is compromised.

**Q4. Why is identity central to Zero Trust?**
Because access decisions are based on who/what is requesting access and the context of that request, rather than simply trusting anything already inside the network.

## Key Takeaways
- Understood the shift from perimeter-based to Zero Trust security models
- Learned the "never trust, always verify" and "assume breach" principles
- Understood micro-segmentation's role in limiting lateral movement
- Learned how identity-based access control and continuous verification work together
