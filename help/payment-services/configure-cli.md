---
title: Command-line configuration
description: After installation, you can configure Payment Services using the Command-line Interface (CLI).
role: Admin, Developer
level: Intermediate
---
# Command-line configuration

After you install Payment Services, you can easily configure it from [within the Admin](configure-admin.md) or via the Command-line Interface (CLI).

## Configure data export

Payment Services combines order data exported from Magento Open Source and Adobe Commerce with aggregated payment data from payment providers to create useful reports. The Payment Services extension uses indexers to efficiently collect all necessary data for the reports.

To learn about the data used in Payment Services reporting, See [Order payment status report](order-payment-status.md#data-used-in-the-report).

### Configure cron on Magento Open Source

If you want to use a `BY SCHEDULE` index mode on Magento Open Source, you must configure cron. See [Configure and run cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Set indexers

Order data is exported and persisted in the Payment Service, using one of two index modes---`ON SAVE` (default) or `BY SCHEDULE` (recommended).

The following indexes are for Payment Services:

|   Code    |   Name    |   Description    |
|    ---    |  ---  |  ---  |
|   `sales_order_data_exporter`    |   Sales Order Feed   |   Builds index of order data  |
|   `sales_order_status_data_exporter`    |   Sales Order Statuses Feed    |    Builds index of sales order statuses data   |
|   `store_data_exporter`    |   Stores Feed    |   Builds index of store data   |

To change the index mode for all three indexers, run:

``` bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>If you don't specify any indexers in your command, all indexers are updated to the same value. If you want to change a specific indexer, you must list it in your command.

To learn more about manually changing the mode of an indexer, see [Configure indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} in the core user guide.

### Manually reindex data

You can manually reindex data, instead of waiting for it to happen automatically. See [Reindex](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} for more information.

When `BY SCHEDULE` mode is set, the system tracks changed entities and the cron job updates the index for them based on a set schedule. See [Run cron from the command line](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [Configure and run cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) to learn how to manually trigger indexation using cron jobs.

### Send reindexed data to payment service

After the data is indexed, it will be sent automatically to Payment Services. You can also manually trigger the process of sending indexed data with this command:

``` bash
bin/magento saas:resync --feed [feedName]
```

Use the following command options:

|   Command    |   Description    |
|  ---  |  ---  |
|   `bin/magento saas:resync --feed [feedName]`    |   Performs a reindexation of the specified feed and sends it to the corresponding service   |
|   `bin/magento saas:resync --no-reindex`    |    Skips indexation and sends unsynced data from the indexes  |

The `--feed` parameter allows you to specify which feed you want to send:

|   Feed    |   Description    |
|  ---  |  ---  |
|    `paymentServicesOrdersProduction`   |   Orders feed in Production mode    |
|    `paymentServicesOrdersSandbox`    |   Orders feed in Sandbox mode    |
|    `paymentServicesOrderStatusesProduction`   |   Order statuses in Production mode    |
|    `paymentServicesOrderStatusesSandbox`   |   Order statuses in Sandbox mode    |
|    `paymentServicesStoresProduction`   |    Stores in Production mode   |
|    `paymentServicesStoresSandbox`  |   Stores in Sandbox mode    |

All data needed for the reports is sent to Payment Services automatically if cron is configured and installed. You can also manually trigger the process of sending cron data to Payment Services.

``` bash
bin/magento cron:run --group payment_services_data_export
```

To learn more about reindexing and indexers, see the [Manage the indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) topic in the developer documentation.