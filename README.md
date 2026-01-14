# helm-kubeai

A Crossplane Configuration package that installs the KubeAI Helm chart with a minimal, stable interface.

## Overview

`helm-kubeai` renders a single Helm release for KubeAI. It exposes only the inputs needed
for chart values, namespace, and release name, keeping the interface stable while allowing full Helm overrides.

KubeAI is an AI Inference Operator for Kubernetes - the easiest way to serve ML models in production.
It provides an OpenAI-compatible HTTP API and supports vLLM, Ollama, FasterWhisper, and other model servers.

## Features

- **Minimal Helm interface**: values and overrideAllValues with stable defaults
- **Predictable naming**: defaults to `<clusterName>-kubeai` in the `kubeai` namespace
- **GitOps friendly**: ships a `.gitops/` deploy chart

## Prerequisites

- Crossplane installed in the cluster
- Crossplane providers:
  - `provider-helm` (>=v1.0.6)
- Crossplane function:
  - `function-auto-ready` (>=v0.6.0)

## Quick Start

```yaml
apiVersion: pkg.crossplane.io/v1
kind: Configuration
metadata:
  name: helm-kubeai
spec:
  package: ghcr.io/hops-ops/helm-kubeai:latest
```

```yaml
apiVersion: helm.hops.ops.com.ai/v1alpha1
kind: KubeAI
metadata:
  name: kubeai
  namespace: example-env
spec:
  clusterName: example-cluster
  values:
    openwebui:
      enabled: true
```

## Key Features of KubeAI

- **OpenAI-compatible API**: Drop-in replacement for OpenAI
- **Multi-model support**: LLMs, Whisper (speech-to-text), embeddings
- **Auto-scaling**: Scale from zero and autoscale based on load
- **Zero dependencies**: No Istio, Knative, etc. required
- **Chat UI**: Includes OpenWebUI integration

## Development

```bash
make render
make validate
make test
```
