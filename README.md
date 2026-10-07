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
