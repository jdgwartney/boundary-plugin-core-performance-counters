# TrueSite Pulse Plugin For Windows Performance Counter

Template plugin for extracting metrics from the Windows Performance Counter

### Prerequisites

|     OS    | Linux | Windows | SmartOS | OS X |
|:----------|:-----:|:-------:|:-------:|:----:|
| Supported |       |    v    |         |      |

### Plugin Setup

This plugin is useable about of the box with an example `counters.json` which contains example counters to collect from the Windows performance counters.

In most instances you may want to customize the metrics that need to be collected by
by the plugin. See section _Modifying Performance Counters Collected_ below which provides an example of customizing the performance counters collected using this plugin as a template.

#### Performance Counter Configuration File

An example configuration file is shown here:

```json
{
   "counters": [
       {
           "counter_name": "\\processor(_total)\\% processor time",
           "multiplier": "0.01",
           "metric_id": "PROCESSOR_PERCENT_PROCESSOR_TIME"
       },
       {
           "counter_name": "\\memory\\% committed bytes in use",
           "multiplier": "1.0",
           "metric_id": "MEMORY_COMMITTED_BYTES_IN_USE"
       },
       {
           "counter_name": "\\physicaldisk(_total)\\% disk time",
           "multiplier": "0.01",
           "metric_id": "PHYSICAL_DISK_PERCENT_DISK_TIME"
       }
   ]
}

```

The description of each of the files is described below.

- `counters` - An array of the performance counter objects that specied what is to be collected.
- `counter_name` - Name of the Windows Performance Counter to collect
- `multiplier` - Value to multiple the `cooked_value` from the `PerformanceCounterSample` type to get the actual metric value
- `metric_id` - Unique metric identifier to use for the collected performance counter. Note if you create a new metric then you should also update the `metrics.json` file located in the respository described in the next section

#### Metrics Configuration File

This configuration file indicates the metric definitions used by this plugin. Description of each of fields can be found [here](http://documentation.truesight.bmc.com/v1/post/metrics)

```json
{
  "PROCESSOR_PERCENT_PROCESSOR_TIME": {
    "defaultAggregate": "AVG",
    "defaultResolutionMS": 1000,
    "description": "Percentage of CPU used",
    "displayName": "Processor % Time",
    "displayNameShort": "Proc % Time",
    "unit": "percent"
  },
  "MEMORY_COMMITTED_BYTES_IN_USE": {
    "defaultAggregate": "AVG",
    "defaultResolutionMS": 1000,
    "description": "Memory committed bytes in use",
    "displayName": "Memory Committed Bytes",
    "displayNameShort": "Mem Comm. Bytes",
    "unit": "bytecount"
  },
  "PHYSICAL_DISK_PERCENT_DISK_TIME": {
    "defaultAggregate": "AVG",
    "defaultResolutionMS": 1000,
    "description": "Physical Disk Percent Disk Time",
    "displayName": "Physical Disk % Time",
    "displayNameShort": "Disk % Time",
    "unit": "percent"
  }
}
```

### Plugin Configuration Fields

|Field Name  |Description                                                          |
|:-----------|:--------------------------------------------------------------------|
|Source      |The source to display in the legend for the performance counter data.|

### Metrics Collected

|Metric Name           |Description|
|:---------------------|:------------------------------|
|Processor % Time      |Percentage of CPU used         |
|Memory Committed Bytes|Memory committed bytes in use  |
|Physical Disk % Time  |Physical Disk Percent Disk Time|

### Dashboards

- Windows Performance Counter

### Modifying Performance Counters Collected

The following section provides an example of modifying the plugin to support different performance counters.

The steps need to customize the plugin are as follows:

1. Forking this GitHub repository.
2. Configuring desired performance counters to collect.
3. Create the metrics definitions associated with the performance counters.
4. Add the new metrics associated with the performance counters to the plugin manifest.
5. Create new dashboard definitions incorporating the new performance counters to be collected.

#### Forking this GitHub Repository


#### Configuring desired performance counters to collect.

#### Create the metrics definitions associated with the performance counters.

#### Add the new metrics associated with the performance counters to the plugin manifest.

#### Create new dashboard definitions incorporating the new performance counters to be collected.

#### Modify `plugin.json`
