---
title: "stack ls"
description: "The stack ls command description and usage"
keywords: "stack, ls"
---

# stack ls

```markdown
Usage:  docker stack ls [OPTIONS]

List stacks

Aliases:
  ls, list

Options:
      --help                  Print usage
      --format string         Pretty-print stacks using a Go template
```

## Description

Lists the stacks.

> **Note**
>
> This is a cluster management command, and must be executed on a swarm
> manager node. To learn about managers and workers, refer to the
> [Swarm mode section](https://docs.docker.com/engine/swarm/) in the
> documentation.

## Examples

The following command shows all stacks and some additional information:

```console
$ docker stack ls

ID                 SERVICES            ORCHESTRATOR
myapp              2                   Kubernetes
vossibility-stack  6                   Swarm
```

### Formatting

The formatting option (`--format`) pretty-prints stacks using a Go template.

Valid placeholders for the Go template are listed below:

| Placeholder     | Description        |
| --------------- | ------------------ |
| `.Name`         | Stack name         |
| `.Services`     | Number of services |
| `.Orchestrator` | Orchestrator name  |
| `.Namespace`    | Namespace          |

When using the `--format` option, the `stack ls` command either outputs
the data exactly as the template declares or, when using the
`table` directive, includes column headers as well.

The following example uses a template without headers and outputs the
`Name` and `Services` entries separated by a colon (`:`) for all stacks:

```console
$ docker stack ls --format "{{.Name}}: {{.Services}}"
web-server: 1
web-cache: 4
```

## Related commands

* [stack deploy](stack_deploy.md)
* [stack ps](stack_ps.md)
* [stack rm](stack_rm.md)
* [stack services](stack_services.md)
