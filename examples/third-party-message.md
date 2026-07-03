# Third-Party Message Leakage Example

## Scenario

A user asks the model to rewrite a message before sending it to a third party. The third party should not see the user's private instruction or the model's packaging explanation.

## Bad example

```text
According to your request, I will tell them in a more polite way: Hello, the previous wording was not appropriate, so I would like to clarify the current situation...
```

## Problem

The third party can infer that the user and model discussed how to package the message. The sentence exposes meta-communication instead of simply delivering the message.

## Good example

```text
Hello, I would like to clarify the current situation and share the next confirmed step.
```
