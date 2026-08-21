# Emper Labs

The Emper ecosystem for building open-source scientific simulations.

This repository provides a unified development workspace containing the core components of Emper.

Instead of cloning each repository separately, this repository can be used to obtain and develop the complete ecosystem as a single workspace.

---

## Ecosystem

The workspace is organized into several independent components:

```text
Emper Labs
│
├── emper-engine
│   └── Core simulation runtime and data-oriented infrastructure
│
├── emper-modules
│   └── Reusable simulation algorithms and domain functionality
│
├── emper-backends
│   └── Platform-specific rendering and compute implementations
│
├── emper-samples
│   └── Applications, experiments, and simulation workloads
│
└── emper-docs
    └── Architecture, design decisions, and technical documentation
```

Each component remains an independent repository and can be developed independently.

This repository provides the workspace that brings them together.

---

## Getting Started

### Clone the complete ecosystem

Clone this repository together with its submodules:

```bash
git clone --recurse-submodules https://github.com/Emper-Labs/Emper-Labs.git
cd Emper-Labs
```

If the repository was cloned without submodules:

```bash
git submodule update --init --recursive
```

---

## Build

The top-level project provides a unified CMake entry point for the ecosystem.

```bash
cmake -S . -B build
cmake --build build
```

The exact build configuration may vary depending on the platform and the components being developed.

---

## Development Workflow

This repository is intended primarily as a development workspace.

A typical workflow is:

```text
Clone workspace
      │
      ▼
Initialize submodules
      │
      ▼
Configure / build
      │
      ▼
Develop a component
      │
      ├── Engine
      ├── Module
      ├── Backend
      ├── Sample
      └── Documentation
      │
      ▼
Build and test
      │
      ▼
Commit changes in the appropriate repository
```

Each component has its own Git history.

Changes should normally be committed to the repository where the change belongs rather than to this workspace repository itself.

---

## Working With Submodules

The directories in this repository are Git submodules.

To update all components to the revisions referenced by this workspace:

```bash
git submodule update --init --recursive
```

To pull newer changes from the individual repositories during development:

```bash
git -C emper-engine pull
git -C emper-modules pull
git -C emper-backends pull
git -C emper-samples pull
git -C emper-docs pull
```

After updating a submodule, the workspace records the new commit of that submodule.

Commit the workspace change when you want the complete ecosystem to reference the new revisions.

---

## Developing a Component

Components are intentionally separated by responsibility.

### Engine

Develop simulation infrastructure and core runtime functionality.

See `emper-engine`.

### Modules

Develop reusable simulation algorithms and domain-specific functionality.

See `emper-modules`.

### Backends

Develop platform- and API-specific implementations.

See `emper-backends`.

### Samples

Build experiments, applications, benchmarks, and validation workloads.

See `emper-samples`.

### Documentation

Record architecture, technical decisions, design reasoning, and development documentation.

See `emper-docs`.

Each repository contains its own documentation and development-specific information.

---

## Why a Unified Workspace?

Emper is designed as a modular ecosystem rather than a single monolithic repository.

Keeping the components as separate repositories provides:

* Independent development
* Clear dependency boundaries
* Smaller repositories
* Reusable components
* Separate release histories
* Easier experimentation

The workspace repository provides the convenience of treating the ecosystem as a single development environment when working across multiple components.

---

## Architecture

The workspace does not define the architecture of the engine itself.

It defines how the repositories are assembled for development:

```text
                  Emper Labs
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
     Engine        Modules       Backends
        │             │             │
        └─────────────┼─────────────┘
                      │
                      ▼
                   Samples
                      │
                      ▼
                  Workloads
```

The individual repositories remain responsible for their own implementation and design.

---

## Contributing

When contributing to Emper, first determine which component owns the change.

A change should generally be made in the smallest repository that can reasonably own the functionality.

For example:

```text
Core runtime problem
    → emper-engine

Reusable simulation algorithm
    → emper-modules

Platform-specific implementation
    → emper-backends

Experiment or application
    → emper-samples

Architecture or technical documentation
    → emper-docs
```

Cross-repository changes are expected when a feature requires coordinated changes.

---

## Keeping the Workspace Up to Date

The workspace records specific commits of each component.

This provides a reproducible combination of the ecosystem at a particular point in development.

When components evolve independently, the workspace can be updated to reference newer revisions.

This allows development environments and experiments to use a known combination of component versions.

---

## Project Status

Emper is under active development.

The architecture and individual components may evolve as new simulation workloads expose real requirements.

The workspace is intended to remain a stable entry point for obtaining and developing the ecosystem even as individual repositories change.

For the current implementation and design details, refer to the documentation and the individual component repositories.

---

## License

Apache License 2.0
