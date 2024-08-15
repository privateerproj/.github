|   |   |
|---|---|
| **Privateer** (noun) _pri·​va·​teer ˌprī-və-ˈtir_ <br> : an armed private ship licensed to attack enemy shipping <br> **also** : a sailor on such a ship | ![Patches the Privateer Pointer](https://github.com/privateerproj/.github/blob/main/profile/patches-small.png) |

# Privateer

Privateer is a test harness designed to harmonize inputs and outputs for any number of validation test packs.

This project is currently maintained by the [FINOS](https://finos.org) Foundation's [Compliant Financial Infrastructure](https://github.com/finos/compliant-financial-infrastructure) Runtime Validation Working Group. Join us on [Slack](https://finos-lf.slack.com/messages/cfi-runtime-validation-wg)!

## Key Concepts

1. **Privateer** - Inspired by Terraform, and built using some of the same open source dependencies, this is an executable that calls plugins based on the user's configuration. This is the ship that we set sail on.
1. **Raids** - These are the plugins that are called by the core. They are responsible for executing the validation tests and returning the results to Privateer. These are the coordinated attacks our ship engages in to earn a living.
1. **Privateer SDK** - This set of logic and tools is used to establish the relationship between Privateer and it's Raids, and it enables various plugins to behave in a similar fashion for harmonized inputs and outputs. Similar to a pirate's code, but more useful— this is the code we live by.
1. **Tactics** - Each Raid will have sets of related Strikes known as Tactics. These are our battle plans, organized based on different security and regulatory policies.
1. **Strikes** - Strikes are complex functions that attempt to validate a specific control or policy. These are the individual attacks that our ship engages in during a Raid: the slashes of our swords and the firing of our cannons!
1. **Movements** - While a Tactic is a set of _Strikes_, a Strike is a set of _Movements_. This allows small sets of logic to be performed sequentially within a Strike, with independent log entries for each step. This is the series of motions leading up to a cannon firing or a boarding party launching.

## Usage

> [!WARNING]
> All automated installation behavior is currently under active development. Until these features are stabilized, please build and organize Privateer and your desired Raids locally.
> Ensure that all executables are given the correct permissions to run.
> Automated installers are expected to be feature complete in or before October 2024.

### Install Privateer, and ensure it is available in your local PATH.

If installed correctly, the command `pvtr -h` will present you with all commands and flags that are available in your installed version.

### Install desired Raids

Raids are installed to `$HOME/privateer/bin` (relative to your operating system).

If installed correctly, all Raids should be listed by the command `pvtr list -a`.

### Configure your execution

> [!IMPORTANT]
> While an infinite number of different Raids can be run together, multiple runs of the same Raid are not currently supported. When this feature becomes available, it may create a breaking-change in how config variables are written.

An example minimal YAML config file should be included with each Raid. To get acclimated, you can run the [Raid Wireframe](https://github.com/privateerproj/raid-wireframe).

Here is the example config file from Raid Wireframe, which you can copy to your development directory:

```yaml
loglevel: Debug
WriteDirectory: sample_test_output
raids:
  SVC:
    tactic: CCC_OS_Security
    username: fake_user
    password: fake_password
```

In this example, we will have all `Debug` level logs included in our output, which will be stored in a local directory named `sample_test_output`.

Multiple raids may be run simultaneously, but we are only running one in this case. The raid name for this example raid is `SVC`.

A `tactic` or `tactics` may be selected based on what is available for the raid. In this case, we will run [all tests that are included](https://github.com/privateerproj/raid-wireframe/blob/main/cmd/root.go#L62-L77) in `CCC_OS_Security`. 

If we wanted to run multiple tactics from the available options, the format would be a YAML list:

```yaml
# alternate example
raids:
  SVC:
    tactics:
      - CCC_OS_Security
      - CCC_OS_Taxonomy
```

Any additional variables that are required by the raid should be supplied within the context of the service.

> [!NOTE]
> The current logic used for reading configuration variables is designed to be compatiable with secret stores, but those features are not yet available in the latest version of Privateer.

### Run Privateer

If your config file is named `my-config.yml`, you can run privateer as follows:

`pvtr sally -c my-config.yml`

A pass/fail message and other essential runtime information will be printed to the terminal. Execution details will be provided in your specified output directory.

## Creating a new Raid

> [!NOTE] Raid generation is currently only supported for Common Cloud Controls component definitions. Extending this is possible, but not currently planned.

### Raid Generation

Required values are `-p`/`--service-path` and `-n`/`--service-name`. 

By default, the raid is generated from the [official template repo](https://github.com/privateerproj/raid-generator-templates). Optionally, you may customize the template directory and specify the local directory path using `--local-templates`.

The service path may be a local path or URL to a properly formatted Common Cloud Controls component definition.

The service name should be the abbreviated name, such as `-n GCS` for "Google Cloud Storage."

The generated raid will be stored in the output directory: `-o`/`--output-path` (default `generated-raid/`).

### Raid Customization

A generated Raid will contain all of the boilerplate code necessary for it to act as a gRPC plugin. It will also be pre-populated with one tactic and "Strikes" corresponding to the controls in the component definition.

Each Strike listed within the tactic is a function that will be called by Privateer when the Raid is executed.

```go
Armory.Tactics = map[string][]raidengine.Strike{
		"CCC_OS_Security": {
			Armory.CCC_OS_C1_TR01,
			Armory.CCC_OS_C1_TR02,
    }
}
```

Strike functions will be named after the associated control. These functions will be pre-populated with the logic necessary for structured logs. Additional "movement" functions will be pre-populated, corresponding to each Test Requirement for the corresponding control.

```go
func (a *SVC) CCC_OS_C1_TR01() (strikeName string, result raidengine.StrikeResult) {
	// set default return values
	strikeName = "CCC_OS_C1_TR01"
	result = raidengine.StrikeResult{
		Passed:      false,
		Description: "All supported network data protocols must be running on secure channels.",
		Message:     "Strike has not yet started.", // This message will be overwritten by subsequent movements
		DocsURL:     "https://maintainer.com/docs/raids/SVC",
		ControlID:   "CCC-Taxonomy-1",
		Movements:   make(map[string]raidengine.MovementResult),
	}

	CCC_OS_C1_TR01_T01_Result := CCC_OS_C1_TR01_T01()
	result.Movements["CCC_OS_C1_TR01_T01"] = CCC_OS_C1_TR01_T01_Result
	if !CCC_OS_C1_TR01_T01_Result.Passed {
		result.Message = CCC_OS_C1_TR01_T01_Result.Message
		return
	}

	// TODO: Additional movement calls go here

	return
}
```

The value `Passed` should be updated if all movements are successful. 

It is advised to update the Strike `Message` value consistently, so that the log entry contains information about the last action performed.

`DocsURL` is optional, but recommended for complex Strikes. This should contain a link to the code, documentation, or other helpful information for users to understand this Strike.

A strike may contain as many Movements as you like. Generated Movements look like this:

```go
func CCC_OS_C1_TR02_T01() (result raidengine.MovementResult) {
	result = raidengine.MovementResult{
		Description: "JokerName must be found in the runtime configuration.",
		Function:    utils.CallerPath(0),
	}
	
	// TODO: Movement logic goes here
	return
}
```

The Movement `Description` should contain information about why that Movement succeeded or failed. Any Movement failure will result in the failure of the Strike and, subsequently, the Raid.

Movement logic may be self-contained, or call out to other helper functions. This is where you as a Raid developer will do most of your work.
