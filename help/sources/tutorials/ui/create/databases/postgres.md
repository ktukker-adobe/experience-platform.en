---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Create a PostgreSQL source connector in the UI
topic: overview
---

# Create a [!DNL PostgreSQL] source connector in the UI

>[!NOTE]
> The [!DNL PostgreSQL] connector is in beta. See the [Sources overview](../../../../home.md#terms-and-conditions) for more information on using beta-labelled connectors.

Source connectors in Adobe Experience Platform provide the ability to ingest externally sourced data on a scheduled basis. This tutorial provides steps for creating a [!DNL PostgreSQL] (hereinafter referred to as "PSQL") source connector using the [!DNL Platform] user interface.

## Getting started

This tutorial requires a working understanding of the following components of Adobe Experience Platform:

*   [Experience Data Model (XDM) System](../../../../../xdm/home.md): The standardized framework by which [!DNL Experience Platform] organizes customer experience data.
    *   [Basics of schema composition](../../../../../xdm/schema/composition.md): Learn about the basic building blocks of XDM schemas, including key principles and best practices in schema composition.
    *   [Schema Editor tutorial](../../../../../xdm/tutorials/create-schema-ui.md): Learn how to create custom schemas using the Schema Editor UI.
*   [Real-time Customer Profile](../../../../../profile/home.md): Provides a unified, real-time consumer profile based on aggregated data from multiple sources.

If you already have a PSQL base connection, you may skip the remainder of this document and proceed to the tutorial on [configuring a dataflow](../../dataflow/databases.md).

### Gather required credentials

In order to access your PSQL account on [!DNL Platform], you must provide the following value:

| Credential | Description |
| ---------- | ----------- |
| `connectionString` | The connection string associated with your PSQL account. The PSQL connection string pattern is: `Server={SERVER};Database={DATABASE};Port={PORT};UID={USERNAME};Password={PASSWORD}`. |

For more information about getting started, refer to this [PSQL document](https://www.postgresql.org/docs/9.2/app-psql.html).

## Connect your PSQL account

Once you have gathered your required credentials, you can follow the steps below to create a new inbound base connection to link your PSQL account to [!DNL Platform].

Log in to <a href="https://platform.adobe.com" target="_blank">Adobe Experience Platform</a> and then select **[!UICONTROL Sources]** from the left navigation bar to access the *[!UICONTROL Sources]* workspace. The *[!UICONTROL Catalog]* screen displays a variety of sources for which you can create inbound base connections with, and each source shows the number of existing base connections associated to them.

Under the *[!UICONTROL Databases]* category, select **[!UICONTROL PostgreSQL DB]** to expose an information bar on the right-hand side of your screen. The information bar provides a brief description for the selected source as well as options to connect with the source or view its documentation. To create a new inbound base connection, select 
**[!UICONTROL Connect source]**.

![](../../../../images/tutorials/create/psql/catalog.png)

The *[!UICONTROL Connect to PSQL]* page appears. On this page, you can either use new credentials or existing credentials.

### New account

If you are using new credentials, select **[!UICONTROL New account]**. On the input form that appears, provide the base connection with a name, an optional description, and your PSQL credentials. When finished, select **[!UICONTROL Connect]** and then allow some time for the new base connection to establish.

![](../../../../images/tutorials/create/psql/connect.png)

### Existing account

To connect an existing account, select the PSQL account you want to connect with, then select **[!UICONTROL Next]** to proceed.

![](../../../../images/tutorials/create/psql/existing.png)

## Next steps

By following this tutorial, you have established a base connection to your PSQL account. You can now continue on to the next tutorial and [configure a dataflow to bring data into Platform](../../dataflow/databases.md).