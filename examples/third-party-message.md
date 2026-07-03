# Third-Party Message Leakage Example

## Scenario

A user asks the model to rewrite a message before sending it to a third party. The third party should not see the user's private instruction or the model's packaging explanation.

## Bad example

```text
According to your request, I will tell them in a more polite way: Hello, the previous wording may not have been ideal, so I would like to clarify the current situation...
```

## Problem

The third party can see that the user and model discussed how to package the message. The sentence exposes meta-communication instead of simply delivering the message.

## Good example

```text
Hello, I would like to clarify the current situation. The main point is that the timeline has not changed, and I will share an update as soon as there is a confirmed next step.
```
