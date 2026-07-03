# Customer Reply Example

## Scenario

A user asks the model to rewrite a customer reply and adds: "Do not make it sound too eager to please."

## Bad example

```text
I have adjusted this so it does not sound too eager to please: We understand your concern, but the current decision remains unchanged.
```

## Problem

The customer should not see the user's tone correction or the model's revision note. The final reply should naturally sound steady, restrained, and professional without exposing how that tone was requested.

## Good example

```text
Thank you for the clarification. We have reviewed the request, and the current decision remains unchanged. If new information becomes available, we can review it and confirm whether it affects the next step.
```
