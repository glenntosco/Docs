# Update or edit existing vendors

## End Point

'CreateOrUpdate' API end point is used to update/edit existing vendors

<mark style="color:green;">`POST`</mark> `https://{tenant_name}.p4warehouse.com/api/VendorApi/CreateOrUpdate`

#### Headers

| Name                                     | Type   | Description    |
| ---------------------------------------- | ------ | -------------- |
| ApiKey<mark style="color:red;">\*</mark> | String | System API key |

#### Request Body

| Name                                   | Type   | Description                            |
| -------------------------------------- | ------ | -------------------------------------- |
| "Id"<mark style="color:red;">\*</mark> | String | Vendor Id number created by the system |

{% tabs %}
{% tab title="200: OK Vendor information has been updated" %}


```json
{
    "$id": "1",
    "VendorCode": "123456",
    "PurchaseOrders": [],
    "ClientId": null,
    "Client": null,
    "CompanyName": "Demo",
    "ProductExpiryAllowance": null,
    "Description": "Test",
    "Logo": null,
    "ReceivingSlipDisclaimer": null,
    "IsGeneratePoBackOrder": null,
    "ContactPerson": "A.Smith",
    "Email": null,
    "Phone": null,
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
    "IsEmailReceivingSlips": false,
    "Address1": null,
    "Address2": null,
    "City": null,
    "StateProvince": null,
    "ZipPostalCode": null,
    "Country": null,
    "AddressHash": "",
    "Id": "a46cc369-4fdd-4af5-9ea7-f79a582f900d",
    "DateCreated": "2023-08-16T14:58:21.7082476+00:00",
    "TypeName": "Pro4Soft.TenantData.Entities.Business.Purchasing.Vendor",
    "TypeNameShort": "Vendor"
}
```
{% endtab %}

{% tab title="401: Unauthorized Incorrect ApiKey" %}

{% endtab %}

{% tab title="404: Not Found Incorrect URL" %}

{% endtab %}

{% tab title="406: Not Acceptable Missing fields" %}

{% endtab %}
{% endtabs %}

## Available fields

```json
    "VendorCode": String
    "CompanyName": String
    "ProductExpiryAllowance": ??
    "Description": String
    "Logo": String
    "ContactPerson": String
    "Email": String
    "Phone": String
    "Info1": String
    "Info2": String
    "Info3": String
    "Info4": String
    "Info5": String
    "Info6": String
    "Info7": String
    "Info8": String
    "Info9": String
    "Info10": String
    "Address1": String
    "Address2": String
    "City": String
    "StateProvince": String
    "ZipPostalCode": String
    "Country": String
```
