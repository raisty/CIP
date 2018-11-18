## CIP Types

There are three types of CIP:

- A **Standard Track CIP** describes any change that affects most or all Core implementations, such as a change to the the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using Core. Furthermore Standard CIPs can be broken down into the following categories. Standards Track CIPs consist of three parts, a design document, implementation, and finally if warranted an update to the [formal specification].
  - **Core** - improvements requiring a consensus fork, as well as changes that are not necessarily consensus critical but may be relevant to “core dev” discussions.
  - **Networking** - includes improvements around devp2p and Light Core Subprotocol, as well as proposed improvements to network protocol specifications of whisper and swarm.
  - **Interface** - includes improvements around client [API/RPC] specifications and standards, and also certain language-level standards like method names and [contract ABIs]. The label “interface” aligns with the [interfaces repo] and discussion should primarily occur in that repository before an CIP is submitted to the CIPs repository.
  - **CRC** - application-level standards and conventions, including contract standards such as token standards, name registries, URI schemes, library/package formats, and wallet formats.
- An **Informational CIP** describes an Core design issue, or provides general guidelines or information to the Core community, but does not propose a new feature. Informational CIPs do not necessarily represent Core community consensus or a recommendation, so users and implementers are free to ignore Informational CIPs or follow their advice.
- A **Meta CIP** describes a process surrounding Core or proposes a change to (or an event in) a process. Process CIPs are like Standards Track CIPs but apply to areas other than the Core protocol itself. They may propose an implementation, but not to Core's codebase; they often require community consensus; unlike Informational CIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in Core development. Any meta-CIP is also considered a Process CIP.

It is highly recommended that a single CIP contain a single key proposal or new idea. The more focused the CIP, the more successful it tends to be. A change to one client doesn't require a CIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

A CIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.
