# P4Warehouse REST API

## Authentication

All REST API calls and queries require system API key. To obtain the key, navigate to Setup > System > User as shown below.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>P4Warehouse Rest API</p></figcaption></figure>

From the list of available users, click on the 'system' user.&#x20;

In the user detail page, click the drop down icon to access API key for your tenant.



{% hint style="info" %}
If this is for a 3PL client, be sure the API is for a user that is specifically assigned to the 3PL client.
{% endhint %}

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>P4 Warehouse Rest API</p></figcaption></figure>

## Endpoints and Requests

API endpoints are organized by resource type. Use different endpoints depending on your API call requirements.

Here are couple example of API endpoints used throughout the P4W system.

#### **'CreateOrUpdate'** and **'DeleteBatch'** follow this pattern:[&#xD;](https://doc1.p4warehouse.com/api/)

```json
https://{tenant_name}.p4warehouse.com/api/{Resource}Api/CreateOrUpdate

https://{tenant_name}.p4warehouse.com/api/{Resource}Api/DeleteBatch
```

Replace {Resource} with Product, Client, Vendor, PickTicket, PurchaseOrder, etc.

Replace `{tenant_name}` with your tenant's domain.

#### **OData**

For querying database, P4W uses OData protocol.[](https://doc1.p4warehouse.com/odata/PickTicket?$expand=)

<pre class="language-json"><code class="lang-json"><strong>"https://{tenant_name}.p4warehouse.com/odata/PickTicket?$expand={Resources&#x26;Parameters}
</strong></code></pre>

&#x20;Replace `{tenant_name}` with your tenant's domain.

All requests produce HTTP response status code.

#### Four Wall Report

FourWallReport endpoint provides a simple way to retrieve full inventory list including individual products quantities.&#x20;

```json
https://{tenant_name}.p4warehouse.com/api/Report/FourWallReport
```

Replace `{tenant_name}` with your tenant's domain.

#### Execute&#x20;

'Execute' endpoint is used in conjunction with Audit reports.&#x20;

## Payload

API calls containing payload utilize JSON format across the board.
