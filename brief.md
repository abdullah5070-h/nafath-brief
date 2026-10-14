Version: NAFATH-V3
Track: Software

## Overview
A government AI chat assistant inside a mobile app depends on six fields working together. Software teams expose the assistant through an API that the app calls. The AI layer uses retrieval to ground answers in approved service information. The mobile app must reach the backend over secure connections, which iOS enforces by default. Networking carries the traffic, and IPv6 supports the growing number of connected devices. Cybersecurity protects the assistant from malicious instructions hidden in user input or retrieved content. Data protection rules decide how chat logs can be stored and reused. A weakness in one field affects the others, so a project manager should see them as one system.

## Software
Semantic Versioning uses MAJOR.MINOR.PATCH numbers to describe changes to a declared public API. The MAJOR version must increase when backward incompatible changes are made, such as removing or changing an endpoint in a way that breaks existing apps. The MINOR version must increase when new backward compatible functionality is added, or when public functionality is marked as deprecated. The PATCH version must increase only for backward compatible bug fixes. Lower numbers reset to zero when a higher one increases.

Resource: Semantic Versioning 2.0.0 - https://semver.org/


## AI
Retrieval-Augmented Generation (RAG) combines a language model with an external knowledge source. Instead of relying only on memorized training data, the system first retrieves relevant passages from a document index and gives them to the model as context. For a government assistant, this lets answers rely on current, approved service documents. The paper presents retrieval as a way to provide provenance and update knowledge, and reports more specific and factual language than a model without retrieval.

Resource: Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks - https://arxiv.org/abs/2005.11401


## Mobile
App Transport Security (ATS) requires iOS app connections to use Transport Layer Security with reliable certificates and ciphers, including TLS 1.2 or later and forward secrecy. If the app calls a plain HTTP endpoint through the standard URL loading system, ATS blocks the connection and prints a console message. Developers can add exceptions in the Info.plist file, but exceptions weaken security, and some need justification during App Store review.

Resource: Preventing Insecure Network Connections - https://developer.apple.com/documentation/security/preventing-insecure-network-connections


## Networking

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
