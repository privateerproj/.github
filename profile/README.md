|   |   |
|---|---|
| **Privateer** (noun) _pri·​va·​teer ˌprī-və-ˈtir_ <br> : an armed private ship licensed to attack enemy shipping <br> **also** : a sailor on such a ship | <img src="profile/patches-small.png" height="300px"> |

# Privateer

Privateer is a test harness designed to harmonize inputs and outputs for any number of validation test packs.

This project is currently maintained by the [FINOS](https://finos.org) Foundation's [Compliant Financial Infrastructure](https://github.com/finos/compliant-financial-infrastructure) Runtime Validation Working Group. Join us on [Slack](https://finos-lf.slack.com/messages/cfi-runtime-validation-wg)!

## Key Concepts

1. **Privateer (Core)** - Inspired by Terraform, and built using some of the same open source dependencies, this is an executable that calls plugins based on the user's configuration. This is the ship that we set sail on.
1. **Raids (Plugins)** - These are the plugins that are called by the core. They are responsible for executing the validation tests and returning the results to Privateer. These are the coordinated attacks our ship engages in to earn a living.
1. **Privateer SDK** - This set of logic and tools is used to establish the relationship between Privateer and it's Raids, and it enables various plugins to behave in a similar fashion for harmonized inputs and outputs. Similar to a pirate's code, but more useful— this is the code all Privateers live by.
1. **Strikes** - Strikes are complex functions attempt to validate a clearly defined control or policy. These are the individual attacks that our ship engages in to perform a Raid: the slashes of our swords and the firing of our cannons.
1. **Tactics** - Each Raid will have sets of related Strikes known as Tactics. At minimum, every Raid should have a `default` Tactic that can executed called by the user. Subsequent Tactics may be organized based on different policies or standards. These are our battle plans.
1. **Movements** - While a Tactic is a set of _Strikes_, a Strike is a set of _Movements_. This allows small sets of logic to be performed sequentially within a Strike, with independent log entries for each step. This is the series of motions leading up to a cannon firing or a boarding party swinging away from the masts.
