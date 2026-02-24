# Privateer Project

Privateer actively interacts with your deployed systems to verify they behave as expected. It tests from both normal user and attacker perspectives to identify security vulnerabilities and misconfigurations that static analysis might miss.

Privateer orchestrates plugin-based tests and provides consistent output according to the [Gemara](https://gemara.openssf.org) specification. This structure allows any number of resources to be subject to any number of assessment requirements.

||||
|---|---|---|
| <img src="https://github.com/privateerproj/.github/blob/main/profile/anvil.svg" alt="anvil" width="100"> | Privateer SDK | provides common logic for Privateer and Plugins |
| <img src="https://github.com/privateerproj/.github/blob/main/profile/ship.svg" alt="ship" width="100" height="100"> | Privateer Core | the main executable that runs plugins based on user configuration |
| <img src="https://github.com/privateerproj/.github/blob/main/profile/map.svg" alt="map" width="100"> | Plugin | execute validation tests and return results to Privateer |
| <img src="https://github.com/privateerproj/.github/blob/main/profile/cannon.svg" alt="cannon" width="100"> | EvaluationSuite | a set of related data allowing control IDs and their requirements to be mapped to one or more assessment steps |
| <img src="https://github.com/privateerproj/.github/blob/main/profile/match.svg" alt="match" width="100"> | AssessmentStep | a specialized function which will analyze a data payload provided at runtime |

|   |   |
|---|---|
| **Privateer** (noun) _pri·​va·​teer ˌprī-və-ˈtir_ <br> : an armed private ship licensed to attack enemy shipping <br> **also** : a sailor on such a ship | <img src="https://github.com/privateerproj/.github/blob/main/profile/patches-small.svg" alt="Patches the Privateer Pointer" width="250" height="250"> |
