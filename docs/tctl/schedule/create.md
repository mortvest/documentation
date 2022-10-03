---
id: create
title: tctl schedule create
sidebar_label: create
description: How to create a Schedule using tctl.
tags:
  - tctl
---

With tctl, create a Schedule like this:

```shell
$ tctl config set version next   # ensure you're using the new tctl
$ tctl schedule create \
    --sid 'your-schedule-id' \
    --interval '5h/15m' \
    --cal '{"dayOfWeek":"Fri","hour":"11","minute":"3"}' \
    --overlap-policy 'BufferAll' \
    --wid 'your-workflow-id' \
    --tq 'your-task-queue' \
    --type 'YourWorkflowType'
```

This Schedule takes action every 5 hours at 15 minutes past the hour and also at 11:03 on Fridays.
It starts a Workflow `YourWorkflowType` on Task Queue `your-task-queue`, giving it a Workflow Id like `your-workflow-id-2022-06-17T11:03:00Z`.
Workflows do not be run in parallel.
If they would other overlap, they are buffered to run sequentially.

See `tctl schedule create --help` for the full set of available options.