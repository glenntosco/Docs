# Create new product

## End Point

'CreateOrUpdate' API end point is used to create new products.

## Create new product

<mark style="color:green;">`POST`</mark> `https://{tenant_name}.p4warehouse.com/api/ProductApi/CreateOrUpdate`

#### Headers

| Name                                     | Type   | Description    |
| ---------------------------------------- | ------ | -------------- |
| ApiKey<mark style="color:red;">\*</mark> | String | System API key |

#### Request Body

| Name                                    | Type   | Description |
| --------------------------------------- | ------ | ----------- |
| "Sku"<mark style="color:red;">\*</mark> | String | Product SKU |

{% tabs %}
{% tab title="200: OK Product created" %}
```json
{} Response
{
    "$id": "1",
    "Sku": "1234",
    "Upc": null,
    "BarcodeValue": null,
    "BarcodeTypeEnum": null,
    "BarcodeType": null,
    "Category": null,
    "Description": "Demo",
    "SubstituteGroup": null,
    "HtsCode": null,
    "CountryOfOrigin": null,
    "ReferenceNumber": null,
    "Reference1": null,
    "Reference2": null,
    "Reference3": null,
    "Components": [],
    "Packsizes": [],
    "ComponentOf": [],
    "InventoryLocations": [],
    "PurchaseOrderLines": [],
    "CustomerReturnLines": [],
    "PickTicketLines": [],
    "ProductionOrderInLines": [],
    "InProductionOrders": [],
    "ProductionOrderOutLines": [],
    "OutProductionOrders": [],
    "MinMax": [],
    "CartonizationResultContents": [],
    "ClientId": null,
    "Client": null,
    "BomWorkflowId": null,
    "BomWorkflow": null,
    "Height": null,
    "Width": null,
    "Length": null,
    "DimsLengthUnitOfMeasureEnum": 10,
    "DimsLengthUnitOfMeasure": "M",
    "Weight": null,
    "FreightClassEnum": null,
    "FreightClass": null,
    "IsHazMat": false,
    "Nmfc": null,
    "CommodityDescription": null,
    "DimsWeightUnitOfMeasureEnum": 1,
    "DimsWeightUnitOfMeasure": "Kg",
    "Cube": null,
    "IsBillOfMaterial": false,
    "IsLotControlled": false,
    "LotPattern": null,
    "IsSerialControlled": false,
    "SerialPattern": null,
    "IsExpiryControlled": false,
    "IsDecimalControlled": false,
    "IsPacksizeControlled": false,
    "IsDiscontinued": false,
    "UnitOfMeasureEnum": null,
    "UnitOfMeasure": null,
    "CartonizationBehaviourEnum": 0,
    "CartonizationBehaviour": "Inherit",
    "IsDetailsControlled": false,
    "IsDetailsAllocatedControlled": false,
    "Info1": null,
    "Info2": null,
    "Info3": null,
    "Info4": null,
    "Info5": null,
    "Info6": null,
    "Info7": null,
    "Info8": null,
    "Info9": null,
    "Info10": null,
    "Id": "adf4902d-f395-409a-b994-10e57478df28",
    "DateCreated": "2023-08-15T14:54:54.2181627+00:00",
    "TypeName": "Pro4Soft.TenantData.Entities.Business.Product",
    "TypeNameShort": "Product"
}
```
{% endtab %}

{% tab title="406: Not Acceptable Missing fields" %}
\[Sku]: The Sku field is required.
{% endtab %}

{% tab title="401: Unauthorized Incorrect ApiKey" %}

{% endtab %}

{% tab title="404: Not Found Incorrect URL" %}

{% endtab %}
{% endtabs %}

Newly created products are assigned with 'Id' number. Use this number to further update/edit selected products.

If payload (JSON) contains 'Id' number, system will update corresponding product. If 'Id' is missing or incorrect, system will automatically create new product.

## JSON Example

Here is an example of a JSON payload to create new product with SKU, description, UPC, dimensions, and additional information.

```postman_json
{
    "Sku":"PRODUCT_1234",
    "Description":"API Demo",
    "Upc": 1153453189302,
    "Height": 18,
    "Width": 4,
    "Length": 10,
    "DimsLengthUnitOfMeasure": "In",
    "Weight": 1,
    "DimsWeightUnitOfMeasure": "Lb",
    "Info1":"Test Information 1",
    "Info2":"Test Information 2"
}
```

For the full list of fields available for product category, please see product edit/update section next.
