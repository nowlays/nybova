# Nybova

### See the endpoint. Understand the behavior. Respond to the incident.

Nybova is an open-source endpoint security project focused on
cross-platform telemetry, behavioral detection and incident response.

Built for Windows and Linux.

---

## Why Nybova?

An endpoint can tell you a lot about an incident.

A process starts.
A child process appears.
A file is created.
A script interpreter executes.
A network connection is established.
An account authenticates.

Individually, these events may be legitimate.

Together, they can describe an attack.

Nybova is built around this idea:

> Security is not only about identifying malicious files.
> It is about understanding what happened on the endpoint.

---

## Project Status

Nybova is currently in its foundation stage.

There is no claim of production-grade EDR capability at this stage.

The current work focuses on building the primitives required for it:

- a reliable event model;
- platform-aware collectors;
- normalized telemetry;
- deterministic detection;
- reproducible tests.

The project will be considered mature only as these foundations become
measurable, testable and documented.

---

## Design Principles

Nybova is built around a small set of engineering principles that shape
both its architecture and its detection model.

### 1. Telemetry before detection

Reliable detection starts with reliable telemetry.

Nybova does not treat the detection engine as the starting point.
The first priority is to collect meaningful endpoint activity and preserve
the context required to understand it.

If the underlying telemetry is incomplete or inconsistent, detection
becomes difficult to trust.

---

### 2. Behavior over signatures

A known malicious file can often be identified by a signature.

Unknown activity is harder.

Nybova therefore places behavioral signals at the center of its security
model. Process relationships, file activity, network connections,
authentication events, and other system activity can provide useful
security context even when no known signature exists.

Signatures can be useful.

They should not be the only source of detection.

---

### 3. Context over isolated events

An individual event rarely tells the whole story.

A process creation event may be completely legitimate.
A file creation event may be completely legitimate.
A network connection may be completely legitimate.

The relationship between those events can be much more informative.

Nybova therefore treats endpoint activity as a sequence of related events
rather than a collection of independent log entries.

The goal is to preserve enough context for the detection and investigation
layers to understand how activity is connected.

---

### 4. Explainable detection

A security alert should be understandable.

Nybova should not simply report:

> Suspicious activity detected.

A useful detection should provide enough context to explain:

- what happened;
- which events contributed to the detection;
- why the activity was considered suspicious;
- which entities were involved;
- what an analyst should investigate next.

Detection logic should therefore remain observable, testable, and explainable.

---

### 5. Platform-specific collection, common security model

Windows and Linux expose different system interfaces and different sources
of security telemetry.

Nybova does not attempt to hide these differences inside the collectors.

Platform-specific components are responsible for understanding their
operating system and collecting the appropriate telemetry.

The rest of the platform should consume a common security-oriented event
model wherever possible.

Windows and Linux collectors should therefore produce normalized events
that can be consumed by the same detection layer.

The goal is to remain cross-platform without pretending that Windows and
Linux expose identical security data.
