# Current Status: Jupyter's Telemetry System.

Jupyter Telemetry: https://github.com/jupyter/telemetry
- Event-logger in Python (soon, Javascript)
    1) Write custom event schemas
    2) Register schemas with the `EventLog`
    3) Record event data, following event schemas, using `EventLog.record(...)`
    4) `EventLog` validates and records data in specified destinations.
- JupyterHub (and soon, Jupyter Server) have EventLog's built-in.


What can you do today?

* Telemetry inside Jupyter Software
    1. Enable telemetry in JupyterHub Server.
    2. Log individual user's (i.e. single-user server) starts/stops.
* Telemetry outside Jupyter Software
    1. Add an `EventLog` to any software and begin recording events.
    2. Write custom event schemas and register them with your custom `EventLog`


What can I do in August 2020?

* Telemetry inside Jupyter Software
    1. Enable telemetry inside individual users' workspaces.
    2. Log individual users' actions on the server (requests to the Server REST API):
        * opening, closing, saving, renaming, etc. files
        * executed code in cells, output from cells.
* Telemetry outside Jupyter Software
    1. Send outside events directly to JupyterHub's `EventLog` through the `api/eventlog` endoint (no need to include a separate EventLog in your software)


What's after that (December 2020)?

1. Enable telemetry in Jupyter frontend/client applications.
    * Log mouse clicks, UI interactions, etc.


## Integrating Jupyter Telemetry Today

JupyterHub and (in August 2020) JupyterLab's Server come with Jupyter Telemetry built-in.

...


## Event Schema Example

Documentation: https://jupyter-telemetry.readthedocs.io/en/latest/pages/schemas.html

```yaml
$id: url.to.event.schema
version: 1
title: Example Event
description: Record this event.
personal-data: true
type: object
properties:
  eventname:
    title: Name
    description: The name of event
    categories:
        - unrestricted
    type: string
  username:
    title: User Name
    description: Identifies the user
    category:
      - personal-identifier
     type: string
required:
- name
```
