# Docker Notes

## Image vs Container

Image:

* Read-only template
* Blueprint for creating containers

Container:

* Running instance of an image
* Has its own writable layer

## Container Lifecycle

Created
↓
Running
↓
Exited
↓
Removed

## What is docker exec?

docker exec allows us to run a command inside an already running container.

Example:

docker exec -it myweb sh

* -i = Interactive
* -t = Allocate terminal
* sh = Shell inside container

## What is the Writable Layer?

Any changes made inside a container are stored in its writable layer.

Examples:

* Creating files
* Installing packages
* Modifying configurations

## Important Learning

A container is essentially a Linux process isolated using namespaces and controlled using cgroups.
