---
title:  Application Security Foundations Level 1 OWASP Edition
author: Tanya Janca
created: Friday 25th November 2022 20:52
Last modified: Friday 25th November 2022 20:52
Aliases: 
Tags: cybersecurity, application-security, appsec
URL: WeHackPurple.com
---
# Application Security Foundations Level 1 OWASP Edition

# Application Security Foundations Level 1 OWASP Edition
By [Tanya Janca](https://twitter.com/shehackspurple)


## General Application Security Program Goals
> Working as an App Sec Eng you'll want to create clear programs for your clients and organizations you work for
1. Inventory
2. Finding Vulnerabilities (ability to release fixes quickly when we need to)
3. The Knowledge to **Fix Security Bugs** that your team finds
	- Dev Education
	- Supporting Documentation
	- Could we eliminate an entire bug class by making a process change?
4. Effective Tooling
	- Before spending money do a proof of concept
	- Just because tools have more advertising dollars doesn't mean they are great
	- Automate with those tools as much as possible (scanning on schedule)
5. Education and Reference Materials for Devs
	- Books, Online Training, FAQ about system
	- Formal Training for Devs, Lunch-Ins
	- Advocacy Program/Security Champions Program
6. Giving Developers Security Tools
7. Security Activities during the SDLC
	- checklists/checkpoint at each point of the SDLC
	- partnership model
8. Incident Response
	- AppSec and Incident Response should work together
	- Incident Response should have preventative measures like logging, alerting, and monitoring
	- Implement tooling to detect incidents
	- Security incident training for all employees
9.  Continuous Improvement- process improvement
	- better tools or better tools that fit for organization budget

## Example Program Goals 1
> Spend 1 year
> First 6 months?
> 2nd 6 months?
> 
1. Scan all web apps with DAST tool
2. Figure out Top 3
3. Provide a lesson on Top 3
4. Create a presentation of those Top 3
5. Try to get critical things addressed- communicate to appropriate POCs

**Note: this is very similar to the internal audit work flow of helping systems reach compliance**

## Example Program Goals 2
1. Code in the same repository
2. AppSec team can run automated security scans and tools
---This could take 6 months of persuasive talks and working with management---
3. Weekly software composition analysis scans
	- secret scanning (hash, password, api key, connection string)
4. Weekly SAST Scans
5. Once the tools have been tuned you can create automation for certain events like finding secrets and creating tickets (be aware of false positives)
6. Penetration Test of the 3 Mission Critical Applications

## Example Program Goals 3
1. 6 months of creating a security champion program
2. Code Reviews of all pushed code
3. Give Secure Code Training to everyone
4. 6 months of threat modeling
5. Provide documentation for devs for secure design
6. Create a best practice document for entire organization

## AppSec Basics

### AppSec Activities Basics

- **VA Scans** are just low hanging fruit DAST scans versus a full blown **VA Assessment or Sec Assessment** conducted by a person, team, third party
- **Threat Modeling**
- **Secure Code Review and SAST (Static Application Security Testing (SAST)**
- **Software Composition Analysis (SCA):** all the 3rd party components, frameworks, plugins, Nuget packages, libraries. All of that code you didn't write is still code that could cause you harm
- **Penetration Testing**

### AppSec Activities Intermediate
- Dev Education and Advocacy Programs: Secure design, coding, architecture
- Responsible Disclosure & Bug Bounties
- Policies, Standards and Guidelines that are _actually useable_.
- Giving Developers Security Tools
- Secure Coding Library/Templates
- Security Reference Materials: providing books, videos, articles and blogs to software developers on security can help you, and them
- Partnership Model: pairing a security professional with each new software project. They follow the entire project, finding all of the security answers
- Metrics and Measurement: being more specific with expectations
- Security Regression Testing (with Unit Tests): 
	- Unit Test- does it do what it's supposed to do
	- Security Tests- what can I make it do that it's NOT supposed to do
	- Regression Testing- retesting everything just changed
	- Negative Unit Tests- putting bad information and making sure the application can handle it and not tricked into doing things it should not do
- Capture the Flag and Gamification: holding CTFs can be a good way to teach devs about security
- Reviewing New Tech: Reviewing all new tools, frameworks, components, platforms, and other tech that the devs want to approve and/or offer security guidance on using them
- IDEs and Security Plug-Ins for those IDEs
- Adding  a shield in front of your app [[Web Application Firewall (WAF)]] and [[Runtime Application Security Protection(RASP)]]

### AppSec Activities- DevOps Flavored
1. Adding Security tooling to a pipeline
2. Asynchronous pipeline- run all the slow tests I want (think testing branch from juiced-bets)
	We should add only our fastest, most accurate, and most important tests to a release pipeline. We should save very slow, inaccurate and less important tests for running outside the pipeline or in an asynchronous pipeline.
3. Chaos Engineering and Read Teaming
	- Blue Team Defends (fix bugs, install WAF, or RASP, fix servers, etc)
	- Red Team Offensive (aggressively test the defenses, ie, pentests, exploits)
4. Security Sprints- catch up on security bug fixes, plan a security activity, and do deep testing during your security sprint
5. Asking for Feedback from Dev & Ops

### AppSec Activities- Advanced
1. Team- Specific customized Security Training
2. Creating Custom Tools- don't make tools just to make tools, only if necessary
3. Bug Bounties
4. Red Teaming
5. Target and Entire Bug Class
6. Table Top Exercise