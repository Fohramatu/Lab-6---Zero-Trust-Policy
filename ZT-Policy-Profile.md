# Lab-6---Zero-Trust-Policy
1. ZTA Component Definitions
Policy Engine (PE)  
The Policy Engine is the main decision-maker in a Zero Trust system. It looks at all the security signals; who the user is, what device they're on, and where the request is coming from and decides whether access should be allowed, denied, or challenged. It acts like the "brain" that evaluates risk before anything is approved.

Policy Administrator (PA)  
The Policy Administrator takes the Policy Engine's decision and turns it into the actual steps needed to enforce it. If the PE decides a user needs MFA or should be denied, the PA sends out those instructions. It's basically the "translator" that converts decisions into actions.

Policy Enforcement Point (PEP)  
The Policy Enforcement Point is the component that physically controls access to the resource. It's the "gatekeeper" that either opens the door or keeps it shut based on what the PE and PA decide. All traffic to the HR PII Database must pass through the PEP.

2. Core Principle Application
Chosen Principle: Verify Explicitly

The Policy Engine enforces Verify Explicitly by checking every access request against real-time conditions instead of trusting anything by default. For example, if an HR employee tries to access the Employee PII Database, the Policy Engine checks their identity, device health, and location. Even if the user has the right credentials, the PE will deny access if the login attempt comes from unverified location. This ensures that access is based on verified signals, not assumptions or past approvals.

3. Simplified Policy Table
Access Policy for HR Employee PII Database

| Policy Requirement (Signal) | Condition to be Met by User | Action if Condition is Met |
|-----|-----|-----|
| User Identity | User must authenticate with MFA and be a member of the HR Security Group. | Grant Access |
| Device Posture | Device must be compliant (patched OS, active endpoint protection, no known vulnerabilities). | Grant Access |
| Network Context | User must connect from an approved geographic region and secure network. | Grant Access |
