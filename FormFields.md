# Form fields

## Bool toggle

```xml
<field name="status" formElement="checkbox">
    <argument name="data" xsi:type="array">
        <item name="config" xsi:type="array">
            <item name="default" xsi:type="number">0</item>
        </item>
    </argument>

    <settings>
        <dataScope>status</dataScope>
        <dataType>boolean</dataType>
        <label translate="true">Status</label>
    </settings>

    <formElements>
        <checkbox>
            <settings>
                <valueMap>
                    <map name="false" xsi:type="number">0</map>
                    <map name="true" xsi:type="number">1</map>
                </valueMap>

                <prefer>toggle</prefer>
            </settings>
        </checkbox>
    </formElements>
</field>
```