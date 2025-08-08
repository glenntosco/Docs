# Retrieve a list of products

## OData

P4W utilizes OData when querying database through API calls. Following example retrieves first 20 products, including assigned clients if applicable.

<mark style="color:blue;">`GET`</mark> `https://{tenant_name}.p4warehouse.com/odata/Product`

Retrieves a list of first 20 products and product assigned clients when possible.

#### Query Parameters

| Name                                       | Type    | Description                                            |
| ------------------------------------------ | ------- | ------------------------------------------------------ |
| $expand<mark style="color:red;">\*</mark>  | String  | Client base                                            |
| $orderby<mark style="color:red;">\*</mark> | String  | SKU                                                    |
| $top<mark style="color:red;">\*</mark>     | Integer | Number of products to retrieve                         |
| $count<mark style="color:red;">\*</mark>   | Boolean | Whether to displays total number of products available |

#### Headers

| Name                                     | Type   | Description    |
| ---------------------------------------- | ------ | -------------- |
| ApiKey<mark style="color:red;">\*</mark> | String | System API key |

{% tabs %}
{% tab title="200: OK " %}


```json
{
    "@odata.context": "https://doc1.p4warehouse.com/odata/$metadata#Product(Client(Id,Name))",
    "@odata.count": 21,
    "value": [
        {
            "Sku": "1234",
            "Upc": null,
            "BarcodeValue": null,
            "BarcodeType": null,
            "Category": null,
            "Description": null,
            "SubstituteGroup": null,
            "HtsCode": null,
            "CountryOfOrigin": null,
            "ReferenceNumber": null,
            "Reference1": null,
            "Reference2": null,
            "Reference3": null,
            "ClientId": null,
            "BomWorkflowId": null,
            "Height": null,
            "Width": null,
            "Length": null,
            "DimsLengthUnitOfMeasure": "M",
            "Weight": null,
            "FreightClass": null,
            "IsHazMat": false,
            "Nmfc": null,
            "CommodityDescription": null,
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
            "UnitOfMeasure": null,
            "CartonizationBehaviour": "Inherit",
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
            "Id": "935bfda9-e615-4966-8606-ac037dfcc3fb",
            "DateCreated": "2023-08-15T18:36:06.3294549Z",
            "Client": null
        },
        {
            "Sku": "PRODUCT_A",
            "Upc": "1153453189306",
            "BarcodeValue": "1153453189306",
            "BarcodeType": "Code128",
            "Category": null,
            ...
```
{% endtab %}
{% endtabs %}

Use OData syntax ([https://www.odata.org/documentation/](https://www.odata.org/documentation/)) to personalize queries through API calls.

### Example of OData query&#x20;

```json
https://{tenant_name}.p4warehouse.com/odata/Product
$expand=Client($select=Id,Name)&$orderby=Sku&$top=20&$count=true
```
