# Katalon Studio SeaLights Plugin

## Purpose
This plugin is for integration with [SeaLights](https://www.sealights.io) to:
- List of excluded test cases that has been analyzed by previous run to reduce the needed to run all test cases.
- Report the test result back to feed for SeaLights Test Analysis.

- This plugin does not include installing SeaLights agent or code instrument to collect test coverage.

## How to use
1. Install the plugin either [offline](https://docs.katalon.com/docs/plugins-and-add-ons/katalon-store/katalon-studio-plugins/installing-plugin-offline-in-katalon-studio#install-plugins-offline) or [via Katalon store](https://docs.katalon.com/docs/plugins-and-add-ons/katalon-store/katalon-studio-plugins/install-plugins-online-from-the-katalon-store)
2. Setup plugin configuration

   <img width="391" alt="sealights_configuration_ui" src="https://user-images.githubusercontent.com/1128/216404017-896458db-973c-4049-a53d-ec0f0fb7c2dc.png">

   - Using SeaLights: Enable or disable SeaLights Plugin.
   - URL: Your SeaLights URL to connect SeaLights server.
   - Agent Token: Agent token generated from the SeaLights server 
   - Lab Id: Unique ID for a set of test labs in case multiple labs are running simultaneously.
   - Test Stage: Name of the test stage.
   - Build Session Id: Session ID of configuration created.
   - Session Timeout (seconds): Test session timeout (by default: 14400).
4. Create dynamic test suite.
When creating dynamic test suite. The plugin will get the exclude test case from SeaLights and generate a list of test cases to run.
5. Execute the created dynamic test suite with either one of two mode below:
    + Inside Katalon Studio:
    It should be only used in testing mode with testing environment do not run this in real environment as it could impact the SeaLights Test Analysis for next run.
    + In command-line mode execution
    #### List Syntax SeaLights
    Default if you don't pass parameters. Then the default value will be taken from within `Katalon Studio` => `Project` => `Settings` => `Plugins` => `Sealights`
    - `-sealightsUrl` : URL connect to SeaLights server (Optional).
    - `-sealightsAgentToken`: Agent Token (Optional).
    - `-sealightsLabId`:  Lab Id (Optional).
    - `-sealightsTestStage`: Test Stage (Optional).
    - `-sealightsBSId`: Build Session Id (Optional). 
    - `-sealightsSessionTimeout`: Session Timeout (default value is 14400) (Optional).

    ** If optional value is not set, It will be default to UI configuration value if it is not set.

#### CLI Example
```
katalonc -noSplash -runMode=console -projectPath="C:\Users\Katalon Studio\Project\YourProject.prj" -retry=0 -testSuitePath="Test Suites/download" -executionProfile="default" -browserType="Chrome" --config -sealightsUrl="your sealights server" -sealightsAgentToken="your sealights agent token"
```


