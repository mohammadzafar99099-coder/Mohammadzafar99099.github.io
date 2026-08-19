# Vulnerability Report Prompt Engineering
## Problem
Naive prompts flatten every security finding to the same level of urgency. A raw scan report handed to a 
non-technical stakeholder gives them no way to decide what to fix first or what to fund.
## What I Did
I built a six-step prompt iteration ladder on a real vulnerability 
scan (Nmap + Nikto output from a lab environment), applying one named technique at
each step: role assignment, context and motivation, few-shot examples, output structure, 
and step decomposition. I ran the final prompt on both Claude and ChatGPT and compared the
real outputs side by side.

## What Came of It
Step decomposition fixed a real accuracy problem on both models - it made the executive summary's 
numbers match the detailed findings underneath it. But the two models diverged in ways worth 
documenting: ChatGPT surfaced its own intermediate reasoning steps as visible headers in the final report,
which would need manual cleanup before sending to a real client, and the two models disagreed
on whether a finding should be rated Critical or High. The result was a reusable prompt template
plus a concrete lesson that prompt engineering technique alone doesn't guarantee model-agnostic output.
