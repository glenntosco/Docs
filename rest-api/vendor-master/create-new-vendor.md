# Create new vendor

## End Point

'CreateOrUpdate' API end point is used to create new vendor.

<mark style="color:green;">`POST`</mark> `https://{tenant_name}.p4warehouse.com/api/VendorApi/CreateOrUpdate`

#### Headers

| Name                                     | Type   | Description    |
| ---------------------------------------- | ------ | -------------- |
| ApiKey<mark style="color:red;">\*</mark> | String | System API key |

#### Request Body

| Name                                           | Type   | Description                        |
| ---------------------------------------------- | ------ | ---------------------------------- |
| "VendorCode"<mark style="color:red;">\*</mark> | String | Vendor number assigned by the user |

{% tabs %}
{% tab title="200: OK Vendor is created" %}
```json
{
    "$id": "1",
    "VendorCode": "123456",
    "PurchaseOrders": [],
    "ClientId": null,
    "Client": null,
    "CompanyName": "Test",
    "ProductExpiryAllowance": null,
    "Description": "Demo",
    "Logo": null,
    "ReceivingSlipDisclaimer": null,
    "IsGeneratePoBackOrder": null,
    "ContactPerson": null,
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
    "Id": "f7476132-b8e2-4ccf-88fc-3c1e82f52414",
    "DateCreated": "2023-08-15T20:37:08.7079073+00:00",
    "TypeName": "Pro4Soft.TenantData.Entities.Business.Purchasing.Vendor",
    "TypeNameShort": "Vendor"
}
```
{% endtab %}

{% tab title="406: Not Acceptable Missing field" %}
```
[VendorCode]: The VendorCode field is required.
```
{% endtab %}

{% tab title="401: Unauthorized Incorrect API key" %}

{% endtab %}

{% tab title="404: Not Found Incorrect URL" %}

{% endtab %}
{% endtabs %}

Newly created vendors are assigned with 'Id' number. Use this number to further update/edit selected vendors.

## JSON Example

Here is an example of a JSON payload to create new vendor with vendor number, description, company name, address, and additional information.

```postman_json
{
   "VendorCode":"1234",
   "Description":"API Demo",
   "CompanyName":"A&B",
   "Address1": "4310 N Whipple",
    "Address2": "5",
    "City": "Chicago",
    "StateProvince": "IL",
    "ZipPostalCode": "60618",
    "Country":"USA",
    "Info1":"Info1",
    "Info2":"Info2"
}
```
