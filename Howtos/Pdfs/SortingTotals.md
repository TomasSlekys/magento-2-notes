# Sorting Totals in Order PDFs

Sort order for totals can be configured via the pdf.xml file in your custom module. The `totals` node allows you to specify the order of the totals that will be displayed in the PDF.

Example file: `vendor/magento/module-sales/etc/pdf.xml`

```xml
<?xml version="1.0"?>
<!--
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Sales:etc/pdf_file.xsd">
    <renderers>
        <page type="invoice">
            <renderer product_type="default">Magento\Sales\Model\Order\Pdf\Items\Invoice\DefaultInvoice</renderer>
        </page>
        <page type="shipment">
            <renderer product_type="default">Magento\Sales\Model\Order\Pdf\Items\Shipment\DefaultShipment</renderer>
        </page>
        <page type="creditmemo">
            <renderer product_type="default">Magento\Sales\Model\Order\Pdf\Items\Creditmemo\DefaultCreditmemo</renderer>
        </page>
    </renderers>
    <totals>
        <total name="subtotal">
            <title translate="true">Subtotal</title>
            <source_field>subtotal</source_field>
            <font_size>7</font_size>
            <display_zero>true</display_zero>
            <sort_order>100</sort_order>
        </total>
        <total name="discount">
            <title translate="true">Discount</title>
            <source_field>discount_amount</source_field>
            <title_source_field>discount_description</title_source_field>
            <font_size>7</font_size>
            <display_zero>false</display_zero>
            <sort_order>200</sort_order>
        </total>
        <total name="shipping">
            <title translate="true">Shipping &amp; Handling</title>
            <source_field>shipping_amount</source_field>
            <font_size>7</font_size>
            <display_zero>false</display_zero>
            <sort_order>400</sort_order>
        </total>
        <total name="adjustment_positive">
            <title translate="true">Adjustment Refund</title>
            <source_field>adjustment_positive</source_field>
            <font_size>7</font_size>
            <display_zero>false</display_zero>
            <sort_order>500</sort_order>
        </total>
        <total name="adjustment_negative">
            <title translate="true">Adjustment Fee</title>
            <source_field>adjustment_negative</source_field>
            <font_size>7</font_size>
            <display_zero>false</display_zero>
            <sort_order>600</sort_order>
        </total>
        <total name="grand_total">
            <title translate="true">Grand Total</title>
            <source_field>grand_total</source_field>
            <font_size>8</font_size>
            <display_zero>true</display_zero>
            <sort_order>700</sort_order>
        </total>
    </totals>
</config>
```

To change the sort order of a total, create a `etc/pdf.xml` file in your custom module and override the `sort_order` attribute for the desired total. The lower the number, the higher the priority in the PDF.

Example:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Sales:etc/pdf_file.xsd">
    <totals>
        <total name="shipping">
            <sort_order>220</sort_order>
        </total>
    </totals>
</config>
```