|   |   |
|---|---|
| **Privateer** (noun) _pri·​va·​teer ˌprī-və-ˈtir_ <br> : an armed private ship licensed to attack enemy shipping <br> **also** : a sailor on such a ship | <img src="https://github.com/privateerproj/.github/blob/main/profile/patches-small.png" alt="Patches the Privateer Pointer" style="max-height: 200px;"> |

# Privateer Project

Privateer is a runtime behavior testing framework designed for security and compliance validation in infrastructure environments. Instead of prescribing specific actions or analyzing static configurations, Privateer actively tests your deployed infrastructure by simulating real-world usage from both typical and malicious users. This approach ensures that only expected behaviors are possible, helping to identify vulnerabilities and misconfigurations that other methods might overlook.

Intended for use in pre-production environments, Privateer verifies that your infrastructure is correctly configured before deployment. Its plugin-based architecture allows for harmonized inputs and outputs, enabling you to validate all specified resources using a single input—no matter how complex your architecture is. This unified approach streamlines the validation process and enhances efficiency.

By employing Privateer's runtime behavior testing, organizations can more effectively ensure security and compliance, reducing risks associated with deploying in complex environments.

## Key Concepts

**Privateer** is an executable test harness that calls plugins based on the user's configuration.

**Privateer SDK** is a set of logic and tools used to establish an efficient, secure, and cohesive collaboration between Privateer and its Raids. The SDK guides and enables plugins, independent of each other, to behave in a unified fashion, creating common standards and practices within separate integrations.

**Raids** are plugins responsible for executing validation tests and returning results to Privateer. Raids can have multiple Tactics.

- **Tactics** are plans created and organized from requirements within Raids. They are evaluated based on different security and regulatory policies. Each Tactic is created from Raids and will have a related set of Strikes.
- **Strikes** are complex functions that attempt to validate a specific control or policy. Each Tactic will have a set of Strikes.
- **Movements** allow small sets of logic to be executed sequentially within a single Strike, with an independent log entry for each step.

### Enhance Infrastructure Validation

Privateer is built with infrastructure engineers in mind. If you need to validate your resources against security or compliance standards, Privateer can help. The user-friendly command line interface and powerful features simplify the complexities of validation.

Avast, it’s time to weigh anchor!

Whether you're looking to deploy existing Raids or embark on crafting new ones, Privateer stands ready to elevate your resource validation journey.