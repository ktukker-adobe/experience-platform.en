---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Configure a dataflow for an advertising connector in the UI
topic: overview
---

# Configure a dataflow for an advertising connector in the UI

A dataflow is a scheduled task that retrieves and ingests data from a source to an Adobe Experience Platform dataset. This tutorial provides steps to configure a new dataflow using your advertising account.

## Getting started

This tutorial requires a working understanding of the following components of Adobe Experience Platform:

-   [Experience Data Model (XDM) System](../../../../xdm/home.md): The standardized framework by which [!DNL Experience Platform] organizes customer experience data.
    -   [Basics of schema composition](../../../../xdm/schema/composition.md): Learn about the basic building blocks of XDM schemas, including key principles and best practices in schema composition.
    -   [Schema Editor tutorial](../../../../xdm/tutorials/create-schema-ui.md): Learn how to create custom schemas using the Schema Editor UI.
-   [Real-time Customer Profile](../../../../profile/home.md): Provides a unified, real-time consumer profile based on aggregated data from multiple sources.

Additionally, this tutorial requires that you have already created a advertising account. A list of tutorials for creating different payment connectors in the UI can be found in the [source connectors overview](../../../home.md).

## Select data

After creating your advertising account, the *[!UICONTROL Select data]* step appears, providing an interactive interface for you to explore your file hierarchy.

- The left half of the interface is a directory browser, displaying your server's files and directories.
- The right half of the interface lets you preview up to 100 rows of data from a compatible file.

Select the directory you wish to use, then select **[!UICONTROL Next]**.

![add-data](../../../images/tutorials/dataflow/advertising/add-data.png)

## Map data fields to an XDM schema

The *[!UICONTROL Mapping]* step appears, providing an interactive interface to map the source data to a [!DNL Platform] dataset.

Choose a dataset for inbound data to be ingested into. You can either use an existing dataset or create a new dataset.

### Use an existing dataset

To ingest data into an existing dataset, select **[!UICONTROL Use existing dataset]**, then click the dataset icon.

![use-existing-dataset](../../../images/tutorials/dataflow/advertising/use-existing-target-dataset.png)

The *[!UICONTROL Select dataset]* dialog appears. Find the dataset you you wish to use, select it, then click **[!UICONTROL Continue]**.

![select-existing-dataset](../../../images/tutorials/dataflow/advertising/select-existing-dataset.png)

### Use a new dataset

To ingest data into a new dataset, select **[!UICONTROL Create new dataset]** and enter a name and description for the dataset in the fields provided.

During this process, you can also enable *[!UICONTROL Partial ingestion]* and *[!UICONTROL Error diagnostics]*. Enabling *[!UICONTROL Partial ingestion]* provides the ability to ingest data containing errors, up to a certain threshold that you can set. Enabling [!UICONTROL Error diagnostics] provides details on any incorrect data that is batched separately. For more information, see the [partial batch ingestion overview](../../../../ingestion/batch-ingestion/partial.md).

When finished, click the schema icon.

![create-new-dataset](../../../images/tutorials/dataflow/advertising/new-target-dataset.png)

The *[!UICONTROL Select schema]* dialog appears. Select the schema you wish to apply to the new dataset, then click **[!DNL Done]**.

![select-schema](../../../images/tutorials/dataflow/advertising/select-existing-schema.png)

Based on your needs, you can choose to map fields directly, or use mapper functions to transform source data to derive computed or calculated values. For more information on data mapping and mapper functions, refer to the tutorial on [mapping CSV data to XDM schema fields](../../../../ingestion/tutorials/map-a-csv-file.md).

The *[!UICONTROL Mapping]* screen also allows you to set *[!UICONTROL Delta column]*. When the dataflow is created, you can set any timestamp field as a basis to decide which records to ingest in scheduled incremental ingestions.

Once your source data is mapped, click **[!UICONTROL Next]**.

![](../../../images/tutorials/dataflow/advertising/mapping.png)

## Schedule ingestion runs

The *[!UICONTROL Scheduling]* step appears, allowing you to configure an ingestion schedule to automatically ingest the selected source data using the configured mappings. The following table outlines the different configurable fields for scheduling:

| Field | Description |
| --- | --- |
| Frequency | Selectable frequencies include Once, Minute, Hour, Day, and Week. |
| Interval | An integer that sets the interval for the selected frequency. |
| Start time | A UTC timestamp indicating when the very first ingestion is set to occur |
| Backfill | A boolean value that determines what data is initially ingested. If *Backfill* is enabled, all current files in the specified path will be ingested during the first scheduled ingestion. If *Backfill* is disabled, only the files that are loaded in between the first run of ingestion and the *Start time* will be ingested. Files loaded prior to *Start time* will not be ingested. |
| Delta Column | An option with a filtered set of source schema fields of type, date, or time. This field is used to differentiate between new and existing data. Incremental data will be ingested based on the timestamp of selected column. |

Dataflows are designed to automatically ingest data on a scheduled basis. Start by selecting the ingestion frequency. Next, set the interval to designate the period between two flow runs. The interval's value should be a non-zero integer and should be set to greater than or equal to 15.

To set the start time for ingestion, adjust the date and time displayed in the start time box. Alternatively, you can select the calendar icon to edit the start time value. Start time must be greater than or equal to your current UTC time.

Select **[!UICONTROL Load incremental data by]** to assign the delta column. This field provides a distinction between new and existing data.

![schedule-interval](../../../images/tutorials/dataflow/databases/schedule-interval-on.png)

### Set up a one-time ingestion dataflow

To set up one-time ingestion, select the frequency drop down arrow and select **[!UICONTROL Once]**. 

>[!TIP] **[!UICONTROL Interval]** and **[!UICONTROL Backfill]** are not visible during a one-time ingestion.

![schedule-once](../../../images/tutorials/dataflow/databases/schedule-once.png)

Once you have provided appropriate values to the schedule, select **[!UICONTROL Next]**.

## Name your dataflow

The *[!UICONTROL Dataflow detail]* step appears, where you must provide a name and an optional description for the dataflow. Select **[!UICONTROL Next]** when finished.

![dataset-flow-details](../../../images/tutorials/dataflow/advertising/dataset-flow-detail.png)

## Review your dataflow

The *[!UICONTROL Review]* step appears, allowing you to review your new dataflow before it is created. Details are grouped within the following categories:

- *[!UICONTROL Connection]*: Shows the source type, the relevant path of the chosen source file, and the amount of columns within that source file.
- *[!UICONTROL Assign dataset & map fields]*: Shows which dataset the source data is being ingested into, including the schema that the dataset adheres to.
- *[!UICONTROL Scheduling]*: Shows the active period, frequency, and interval of the ingestion schedule.

Once you have reviewed your dataflow, click **[!UICONTROL Finish]** and allow some time for the dataflow to be created.

![review](../../../images/tutorials/dataflow/advertising/review.png)

## Monitor and delete your dataflow

Once your dataflow has been created, you can monitor the data that is being ingested through it. For more information on how to monitor and delete your dataflow, see the tutorial on [monitoring and deleting dataflows](../monitor.md).

## Next steps

By following this tutorial, you have successfully created a dataflow to bring in data from a marketing automation system and gained insight on monitoring datasets. Incoming data can now be used by downstream [!DNL Platform] services such as [!DNL Real-time Customer Profile] and [!DNL Data Science Workspace]. See the following documents for more details:

- [Real-time Customer Profile overview](../../../../profile/home.md)
- [Data Science Workspace overview](../../../../data-science-workspace/home.md)

## Appendix

The following sections provide additional information for working with source connectors.

### Disable a dataflow

When a dataflow is created, it immediately becomes active and ingests data according to the schedule it was given. You can disable an active dataflow at any time by following the instructions below.

Within the *[!UICONTROL Dataflows]* screen, select the name of the dataflow you wish to disable.

![browse-dataset-flow](../../../images/tutorials/dataflow/advertising/view-dataset-flows.png)

The *[!UICONTROL Properties]* column appears on the right-hand side of the screen. This panel contains an **[!UICONTROL Enabled]** toggle button. Click the toggle to disable the dataflow. The same toggle can be used to re-enable a dataflow after it has been disabled.

![disable](../../../images/tutorials/dataflow/advertising/disable.png)

### Activate inbound data for [!DNL Profile] population

Inbound data from your source connector can be used towards enriching and populating your [!DNL Real-time Customer Profile] data. For more information on populating your [!DNL Real-time Customer Profile] data, see the tutorial on [Profile population](../profile.md).
