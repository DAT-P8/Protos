# Protos

This repository contains the `.proto` definitions that model and coordinate multiple simulation systems. These files define the data structures and service interfaces shared between components.

They serve as the contract between the `PyADRL` and `Simulation` projects, ensuring consistent communication across services.


# gRPC

gRPC is a high-performance, open-source Remote Procedure Call (RPC) framework developed by Google. It enables services to communicate with each other as if they were calling local functions, even when running on different machines.

gRPC uses Protocol Buffers as its default interface definition language and message serialization format. From the `.proto` files, it generates strongly-typed client and server stubs in multiple programming languages, enabling type-safe, cross-language communication.


# Protocol Buffers (Protobuf)

Protocol Buffers (Protobuf) is a language-neutral, platform-neutral mechanism for serializing structured data. It allows you to define message schemas in `.proto` files, which can then be compiled into code for various languages.

Compared to formats like JSON or XML, Protobuf is more compact, faster to serialize/deserialize, and enforces a strict schema, making it well-suited for high-performance distributed systems.
