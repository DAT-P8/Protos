# Protos

This repository contains the [Protocol Buffer](https://protobuf.dev/) (proto3) definitions for the GridWorld simulation gRPC service.

## What is this?

`Protos` defines the shared message types and service interface used for communicating with the GridWorld simulation server. Any client or server that interacts with the simulation should use these definitions to generate language-specific gRPC stubs.

## GridWorld Simulation

The simulation models a grid world where drones move around and interact. Drones can be either **evaders** or **pursuers**, and the simulation ends when a termination condition is met (e.g. the evader reaches its target, is destroyed, or flees).

### Actions

Each drone may take one of the following actions per step:

| Action    | Description              |
|-----------|--------------------------|
| `NOTHING` | Stay in place            |
| `LEFT`    | Move left                |
| `RIGHT`   | Move right               |
| `UP`      | Move up                  |
| `DOWN`    | Move down                |

Diagonal movement is not supported.

### gRPC Service (`GWSimulation`)

| RPC       | Request            | Response            | Description                                      |
|-----------|--------------------|---------------------|--------------------------------------------------|
| `New`     | `GWNewRequest`     | `GWNewResponse`     | Start a new simulation; returns initial state and a unique simulation ID |
| `DoStep`  | `GWActionRequest`  | `GWActionResponse`  | Advance the simulation by one step with the given drone actions |
| `Reset`   | `GWResetRequest`   | `GWResetResponse`   | Reset an existing simulation to its initial state |
| `Close`   | `GWCloseRequest`   | `GWCloseResponse`   | Close a simulation and free its resources        |

## Files

| File               | Description                                  |
|--------------------|----------------------------------------------|
| `grid_world.proto` | All message and service definitions          |
| `main.proto`       | Entry point that imports `grid_world.proto`  |

## Usage

Use the `.proto` files to generate gRPC client/server code for your language of choice. The C# namespace is set to `GWSimulation`.

```bash
# Example: generate C# stubs (requires the grpc-tools NuGet package or the gRPC C# plugin)
protoc --csharp_out=. --grpc_out=. \
  --plugin=protoc-gen-grpc=<path-to-grpc_csharp_plugin> \
  grid_world.proto
```
