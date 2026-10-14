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
IPv4 addresses are 32 bits long, while IPv6 addresses are 128 bits long. This gives IPv6 a much greater number of addressable nodes, more levels of addressing hierarchy, and simpler automatic address configuration. IPv6 also simplifies the packet header and uses extension headers for optional information. As the number of connected devices grows, the larger space supports them without heavy reliance on address translation. The standard notes that this makes endpoints more visible, which raises privacy considerations.

Resource: RFC 8200 - Internet Protocol, Version 6 (IPv6) Specification - https://www.rfc-editor.org/rfc/rfc8200


## Cybersecurity
Prompt injection happens when input changes a language model's behavior in unintended ways. In direct injection, the user's own prompt causes this. In indirect injection, the model reads external content, such as a website or file, containing hidden instructions. Two ways to reduce the risk are least-privilege access, which limits what the model can do, and input and output filtering. OWASP notes that no method is guaranteed to prevent it.

Resource: LLM01:2025 Prompt Injection - https://genai.owasp.org/llmrisk/llm01-prompt-injection/


## Data
Pseudonymization replaces direct identifiers, such as a name with a user ID, but the data can still be linked back to a person using additional information. Under the GDPR it remains personal data, so data protection rules still apply. Anonymization makes the person no longer identifiable, considering all means reasonably likely to be used. Only anonymous information falls outside data protection law. For chat logs, pseudonymization helps but does not remove legal duties.

Resource: Regulation (EU) 2016/679 (GDPR), Recital 26 - https://eur-lex.europa.eu/eli/reg/2016/679/oj


## Misconception in My Track
A common wrong belief is that marking a feature as deprecated requires a MAJOR version increase. The correct rule is that deprecation is announced in a MINOR release. The MAJOR increase comes later, when the functionality is actually removed in a backward incompatible way. This gives users time to move to the new API. Evidence: the Semantic Versioning Specification (SemVer) section, item 7, covers the minor version and deprecation.

## Open Question
Does a change in the assistant's answers, such as a new model or retrieval source, count as a breaking API change under SemVer? I would check how major API providers version behavior changes that do not alter the API structure.
