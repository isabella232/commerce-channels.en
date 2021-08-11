---
title: Price Priority Logic
---

# Price priority logic

In the example below, how does the system determine if we should publish $31.99, $24.99, or $27.99?

![](assets/amazon-price-scope.png)

To determine which price will be used if a product is on two websites and has a varying price per website, we use price priority logic (determined by the [Sort Order](https://docs.magento.com/user-guide/stores/stores-all-create-view.html) value).

To view your stores' sort order, go to **Stores** > **All Stores** in the _Admin_ sidebar. In the _Web Site_ column, click the website name. The _Web Site Information_ page shows the _Sort Order_ setting for the website, which determines the priority of the website. A value of `1` indicates the highest priority.

If the product price is set to `Use Default`, it will fall back to the default price value instead of the website price value.

## Example 1

||[Website Priority](https://docs.magento.com/user-guide/configuration/scope.html)|Price (Website)|Use Default|
|---|---|---|---|
|Default|0|$31.99|--|
|Store 1|1|$24.99|No|
|Store 2|2|$27.99|Yes|

- The **Magento Price Source** (defined in your [Listing Price](./listing-price.md) is set to the `Price` attribute.
- Look at the website with the highest website priority, which is Store 1 (defined by the [Sort Order](https://docs.magento.com/user-guide/stores/stores-all-create-view.html) value).
- Since Store 1 is set to use the website price (Use Default = No), the published price will be $24.99.

## Example 2

||[Website Priority](https://docs.magento.com/user-guide/configuration/scope.html)|Price [Website]|Use Default|
|---|---|---|---|
|Default|0|$31.99|--|
|Store 1|1|$24.99|Yes|
|Store 2|2|$27.99|No|

- The **Magento Price Source** (defined in your [Listing Price](./listing-price.md) is set to the `Price` attribute.
- Look at the website with the highest website priority, which is Store 1 (defined by the [Sort Order](https://docs.magento.com/user-guide/stores/stores-all-create-view.html) value).
- Since Store 1 **is not** set to use the website price (Use Default = Yes), look at the next website in the sort order.
- Since Store 2 **is** set to use the website price (Use Default = No), the published price will be $27.99.

## Example 3

||[Website Priority](https://docs.magento.com/user-guide/configuration/scope.html)|Price [Website]|Use Default|
|---|---|---|---|
|Default|0|$31.99|$30.00|
|Store 1|1|$24.99|--|
|Store 2|2|$27.99|$20.00|

In this example we have added in the non-price value, which is used if you select another value for the **Magento Price Source** (defined in your [Listing Price](./listing-price.md) settings). The non-price value will always use price as the fallback price.

- The **Magento Price Source** (defined in your [Listing Price](./listing-price.md) settings) is set to `Non-Price`.
- Look at the website with the highest website priority, which is `Store 1`(defined by the [Sort Order](https://docs.magento.com/user-guide/stores/stores-all-create-view.html) value).
- Since Store 1 **is not** set to use the `Non-Price` attribute, look at the next website in the sort order.
- Since Store 2 **is** set to use the `Non-Price` attribute (Non-Price [Website] = $20.00), the published price will be $20.00.