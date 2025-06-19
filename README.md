# AI Function Call Benchmarking & PII Redaction System

## Overview

This project simulates a benchmarking environment for testing function call accuracy, latency, and security in an AI assistant-like setting. It includes:

- Function call validation for user input
- PII detection and redaction
- Role-based access control (e.g., admin vs analyst)
- Alert generation based on configurable performance thresholds

## Features

### Function Schema
Supports simulation of three core functions:
- `record_orientation_time`: Logs time-related answers
- `record_memory_issue`: Captures memory-related concerns
- `flag_self_harm`: Flags self-harm intent with severity

###  Redaction
Detects and hashes the following:
- Social Security Numbers (format: XXX-XX-XXXX)
- Phone numbers (10 digits)
- Simple names (First Last format)

### Role-Based Access Control
- `admin`: Can view raw user input (including PII)
- `analyst`: Sees redacted/hashes instead

### Alerts and Thresholds
Monitors and flags if:
- Token usage > 3000
- Function fail rate > 10%
- Function call fail rate > 20%
- P95 latency > 1.5s
- Critical failure (e.g., missed self-harm flag)

## How It Works

1. Simulates a few AI conversations using predefined prompts and expected behaviors.
2. Mocks language model response (latency, token use, function called).
3. Checks if function name and arguments match expected.
4. Redacts PII unless the role is `admin`.
5. Logs all events and prints alerts for threshold violations.
