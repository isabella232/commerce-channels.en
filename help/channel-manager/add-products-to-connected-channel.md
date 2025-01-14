---
title: Add products to connected channel
description: Create product assortment for Marketplace sales by adding products from the catalog to the sales channel
exl-id: 00932df7-bdc7-42a1-b269-88dffcc918bc
---

# Add products to connected channel

To sync products to the Walmart Marketplace sales channel, you select products from the [!DNL Commerce] product catalog and import them to Channel Manager. The selected products must have the following attribute configuration:

- **[!UICONTROL Publish to Channel Manager]** attribute is enabled

- At least one product attribute must match one of the [required Walmart Marketplace attributes](map-product-attributes-for-matching.md)–GTIN, ISBN, ISSN, UPC, EAN

The process to import products from [!DNL Commerce] to Channel Manager can take up to 30 minutes or more depending on how many products you select.

## Add products to sales channel

1. From a connected sales channel store, select **Add products** to open the product catalog.
   
   ![Add products to connected channel](assets/add-initial-products-to-connected-channel.png)

   The catalog opens in a new tab.

1. From the catalog product grid, select products to sell on [!DNL Walmart Marketplace].

   ![Send products to the connected channel](assets/select-products-from-catalog.png)

1. Enable the **[!UICONTROL Publish to Channel Manager]** attribute for the selected items.

   - From **[!UICONTROL Actions]**, select **[!UICONTROL Update attributes]**.

   - Scroll to the **[!UICONTROL Publish to Channel Manager]** attribute and enable it.

   - Verify that the product attributes include at least one of the required Walmart Product IDs.

   - Select **[!UICONTROL Save]**.

    A confirmation message displays.

     ![Product import from catalog to sales channel confirmation message](assets/product-import-from-catalog-confirmation.png)

     If the message indicates that the update is scheduled, use the [queue:consumers:start](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-queue.html) [!DNL CLI] command to process the update immediately.

     ```bash
     $ bin/magento queue:consumers:start product_action_attribute.update
     ``` 
  
1. Return to the connected sales channel in [!DNL Channel Manager].

1. After the import operation completes, view products from **[!UICONTROL Listings]**.

   ![Products imported to connected sales channel](assets/products-in-marketplace-sales-channel.png)

   Initially, the products are in *Draft* status. Select **[!UICONTROL Refresh products]** to update the table.
   
