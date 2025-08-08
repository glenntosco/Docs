---
description: P4 Warehouse Change Log
cover: .gitbook/assets/shutterstock_64776388.jpg
coverY: 196.0352422907489
---

# P4 Warehouse Change Log

![P4 Warehouse - The WMS of the Future](.gitbook/assets/logo_inside.png)

**2.15.6**&#x20;

* &#x20;Added a way to pre-rate one line orders to optimize small parcel shipping&#x20;
* Added One Scan shipping for small parcel/e-comm orders&#x20;
* Added a new Configurations section that controls various flavours of One Scan shipping&#x20;

**2.15.5**&#x20;

* Added Driver name to Pick ticket while shipping for private fleet/external&#x20;
* Allowed assigning carrier on Pick ticket&#x20;
* Added Tax Id to Carrier&#x20;
* Extended precision of Rate on Billing Rule to allow small fractional rates (6 decimal points)&#x20;
* Added a new feature which allows holding specific inventory from allocation to a user&#x20;

**2.15.4**&#x20;

* Added a way to assign LPNs to Totes on Shipping Station screen for various carriers without having to do that on Handheld&#x20;
* Added a way to use @Rate variable on 3PL Billing Profiles&#x20;
* Some advanced 3PL Billing profile screens were hidden by default to prevent users from making unintended changes&#x20;
* Added detailed inventory report which surfaces quantity and detailed information like lots, serials and packsizes&#x20;
* Surfaced attribute control visibility on product list&#x20;
* Added a way to designate Client to Custom Action&#x20;

**2.15.3**&#x20;

* Added new Daily inventory snapshot report that records inventory for the passed 60 days&#x20;
* Added configuration which allows failed upload document to be re-uploaded again for a certain number of attempts&#x20;

**2.15.2**&#x20;

* Added Email notification settings to a customer level. Emailing Packslips, BOLs, RMAs&#x20;

**2.15.1**&#x20;

* Added support for latest Android SDK version&#x20;
* Updated Handheld API to allow new permissions for Photo capture&#x20;

**2.14.5**&#x20;

* Added Password policy support&#x20;
* Added automated password expiration and recovery&#x20;

**2.14.4**&#x20;

* Added new settings to Customer/Client/Global which control whether Carton content labels are required&#x20;
* Added new settings to Customer/Client/Global which control whether to print Packslip upon generating a Carrier label&#x20;
* Enhanced security by adding Access controls to module details screen&#x20;
* Added failed login throttling&#x20;

**2.14.3**&#x20;

* Added Pallet printing template and ability to print pallets from Staging/Truckload/Pickticket views
* Added configuration which controls aggregator for pallet numbering&#x20;
* Added configuration on customer/client/global levels which control whether pallets are required to be printed
* Added expiry inbound and outbound allowances on a product level&#x20;
* Added UoM column to expiry grid&#x20;

**2.14.2**&#x20;

* Added additional dropship information on Pickticket header and line level&#x20;
* Reworked Webhook, multiple webhooks are not supporting including Client specific Webhooks
* Added additional check to document level to prevent duplicated document numbering&#x20;

**2.14.1**&#x20;

* Changed allocation precedence in bulk bins from LPN name to LIFO&#x20;
* Added Gauges to reporting&#x20;
* Extended Dashboard filter capabilities to support multiple data types (date, string, number)&#x20;
* &#x20;Added support for additional columns in grids (Currency, Percentage)&#x20;
* Added additional Handheld screen - Tote content

**2.13.1**&#x20;

* &#x20;Android 13 support (API level 33)&#x20;
* Added stage location contents lookup

**2.12.3**

* &#x20;Added Four wall report&#x20;
* &#x20;Added configurations that control which information is sycnrhonzed and shown on Four wall report

**2.12.2**

* &#x20;Added enhanced production options

**2.12.1**

* &#x20; -Added scannable Tracking number to Customer Returns    &#x20;
* \- Added a new Carrier Pickup handheld screen     &#x20;
* \- In addition to SKU and UPC, added a facility to scan BarcodeValue of a Product      &#x20;
* &#x20;Upgraded to a newer version of OS (31)

&#x20;   **2.11.9**

* Added additional mapping for Receiving slip&#x20;
* Improved UI when creating Scheduled Reports&#x20;
* Opened Comments field for changes on PO closure&#x20;
* Added Comments on Receiving slip
* Added additional mapping for Receiving slip&#x20;
* Improved UI when creating Scheduled Reports&#x20;
* Opened Comments field for changes on PO closure - Added Comments on Receiving slip

**2.11.8**&#x20;

* Added 'Auto ship small parcel' flag on a user level&#x20;

**2.11.7**&#x20;

* Improved Ecom dashboard to support unallocated single unit parcels&#x20;
* Added ability to set carton packsize in Ecom dashboard&#x20;
* Improved Small parcel screen which now allows to scan/change Carton size&#x20;

**2.11.6**&#x20;

* Added Scheduled reports&#x20;
* Added additional fields and configurations to enrich comercial invoice report&#x20;

**2.11.5**

* Added history visibility to Packsizes&#x20;
* Added a way to handle totes by carrier tracking number&#x20;
* Added Ecom dashboard, a new way of processing single line, single unit SmallParcel orders in bulk&#x20;
* Added actionable KPIs to E-comm dashboard and Pickticket list&#x20;
* Improved Inventory visility and added Task generation controls on Product details screen&#x20;

**2.11.4**&#x20;

* Improved Malvern integration. Added address verification and rating for Residential deliveries&#x20;
* Improved Tote staging processing while shipping using small parcel&#x20;
* Added new report type: Commercial Invoice that is available for both Pick tickets and Totes &#x20;
* Added automatic printing of Commercial invoices for international shipments if carrier cannot do electric submission&#x20;
* Extended Packsize breakdown to allow breaking to inner packs&#x20;



**2.11.3**&#x20;

* Added a facility to import and export bundle components&#x20;
* Improved UI for bundle components management&#x20;



**2.11.2**&#x20;

* Introduced configuration which controls whether BOL/MBOL could be shipping without charge terms&#x20;
* Added precedence facility to shipping rules when a Pick ticket resolves to more than one rule&#x20;
* Added infrastructure which allows pick ticket small parcel changes to propagate to totes&#x20;



**2.11.1**&#x20;

* Added collection of Dims/Weight on production&#x20;
* Improved truck load shipping verifications&#x20;
* Prevent changing shipping method after order has been shipped&#x20;



**2.10.2**&#x20;

* Removed excessive links for non Administrator users&#x20;
* Changed Apply tags screen to be more user friendly&#x20;
* Created restock user task automation for min/max bins&#x20;



**2.10.1**&#x20;

* Discontinued Kitting, Production should be used instead&#x20;
* Reworked 3PL Billing&#x20;
* Added a way to copy shipping settings to totes from pick ticket&#x20;
* Added a way to create custom 3PL invoice templates&#x20;
* Added a way to pick multiple Picktickets using Full Pack Picking at the same time

**2.09.2**

* Modified UI to aid with long running operations&#x20;
* Improved performance of shipping of BOLs and Master BOLs&#x20;
* Optimized and improved visibility of Auto picking for e-commerce orders

**2.09.1**

* Introduced a new step in Small Parcel shipping: Carrier pickup and manifest&#x20;
* Removed redundant link between Truck Loads and Pick tickets&#x20;
* Removed unused 'Mark for cycle count' option on Handheld skipping&#x20;
* Added a new way to auto generate truck loads based on grouping algorithm

**2.08.6**

* Added 'History search' utility which allows searching deleted records&#x20;
* Moved 'Export to XLSX' and 'Reset Grid' button further apart &#x20;
* Moved ability to build packsizes duriong production&#x20;
* Added ability to suspect orders that were shorted during picking&#x20;
* Added two additional fields to pick ticket&#x20;
* Appt number and Appt date&#x20;
* Relaxed restriction on Production orders to have duplicate Consume/Produce lines

**2.08.5**

* Introduced a new configuration setting which controls whether shorted orders are allowed to be shipped&#x20;
* Added Bill To information to Shipping rules

**2.08.4**

* Introduced a shipping options default facility based on shipping rules (client/customer/scac/zip)&#x20;
* &#x20;Per above, removed all shipping related default that used to be setup on the customer level&#x20;
* Allowed multiple pick tickets (same customer/address) to be full pack picked to the same pallet&#x20;
* Added Bin quarantine override for allocation&#x20;
* QR Code scanning is always enabled for 'sa' user

**2.08.3**

* Added a way to create custom Packslip/Proforma/Receiving/RMA reports&#x20;
* Above reports could be applied to Tenant -> Client -> Customer/Vendor

**2.08.2**

* Added LotNumber field to PO line to force receiving specific lots&#x20;
* Added a set of configurations which controls allowing custom document numbering&#x20;
* Upgraded to a newer version of EasyPost api

**2.08.1**&#x20;

* &#x20;Optimized performance of full pack picking&#x20;
* &#x20;Improved cartonization screen, added additional relevant columns&#x20;
* Implemented new mobile app versioning to support Update notification



**2.07.1**&#x20;

* Emergency fix to Handheld to supress new version check&#x20;
* Extension to Production&#x20;
* Surfaced additional fields on Production List to show finished/disassembled product&#x20;

**2.06.1**&#x20;

* Reworked Production module. Old production is now Kitting
* Added additional handheld screens to support new production&#x20;
* Added additional configurations that drive production&#x20;
* Move Workflows to Setup &#x20;

**2.05.1**&#x20;

* General cumulative fixes&#x20;

**2.04.1**&#x20;

* Enabled ability to do packsize breakdown to an LPN instead of a pickable bin&#x20;

**2.03.1** &#x20;

* Additional work to enable Malvern shipping&#x20;
* Improved performance while handling large, cartonized orders

**2.02.1**&#x20;

* Added Commercial Invoice generation for Small Parcel shipping
* Added a way to reprint Commercial invoice from Web UI 2.01.2
* Major version update
* Substantial changes to backend infrastructure
* Address change to Subdomains
* Added Direct Move Bin suggestion flag will propose bins on product moves

**1.45.1**

* Added configuration that controls maximum ordered quantity for full pack picking
* Improved performance of Pick Ticket details screen

**1.44.1**

* Added quoted weight fields to capture quoted shipping costs
* Added invoiced weight/cube fields to capture actual invoiced costs
* Added Print LPNs option on Staging LPNs screen
* Improved Cartonization performance for order needed a large number of boxes

**1.43.1**

* Extended Lot allocation capabilitiles on Pick Ticket line level
* Added Background allocation for Packsize breadkdown/LPN Letdown to improve performance

**1.42.1**&#x20;

* &#x20;Added a way to record an invoice number when capturing shipping costs on Truck load&#x20;
* Added a configuration Client/Customer/Vendor which controls Back order creation for PO/Pick tickets&#x20;

**1.41.1**&#x20;

* Added additional fields to product master needed to generate customs documentation&#x20;
* Added automatic Packslip and Truckload printing&#x20;

**1.40.1**&#x20;

* Added a facility to track quoted and actual shipping costs for Truck Loads&#x20;
* Added a way to add additional shipping options (Residential, SOD, etc...) for small parcel&#x20;

**1.39.1**

* Added expanded set of configuration for Small Parcel shipping&#x20;
* Added 3rd Party shipping/billing options &#x20;
* Added various payment types when shipping Small Parcel &#x20;
* Added ability to support international shipping using Int. Tax Id&#x20;

**1.38.1**&#x20;

* Added Malvern small parcel shipping broker - Moved Malvern/EasyPost small parcel configuration to a client level

1.37.2

* Fixed Directed putaway query to consume different parameters
* Fixed Android GPS collection when screen goes/device goes to sleep

**1.37.1**&#x20;

* &#x20;Added an option to Unpick whole Pick tickets instead of just one Tote&#x20;
* Added a facility to assign zones and bins to a client&#x20;
* &#x20;Added a facility to specify allowed product categories for zones/bins&#x20;
* Added Receiving Put-a-way Bin suggestion flag - will propose bins during PO receiving
* Added Returns Put-a-way Bin suggestion flag - will propose bins during RMA receiving&#x20;
* Added section to Configuration which contains SQL queries that drive put-a-way logic
* Added Production Workflow management&#x20;
* &#x20;Added Workflow designer and ability to assign workflows to BOM/Client&#x20;

**1.36.1**&#x20;

* Moved Audit records from Mongo DB to SQL for easier reporting
* Added ShipTo name in Pick ticket/Tote selection while building Truck loads&#x20;
* Added Staging LPNs report for visibility into truck load planning&#x20;
* Added a setting which controls whether a BOL document could be printed without signature or not .&#x20;

**1.35.1**&#x20;

**-** Added ability to restrict expiring product on PO and RMA Receiving&#x20;

\- Added additional configuration settings that control expiry allowance&#x20;

\- Added settings to Vendor and Customer that control expiry allowance&#x20;

**1.34.1**&#x20;

* Added Percentage picked to Pick ticket header
* Added a 'Back to Picking' function which allows taking shorted Rating orders back to picking
* Added new Handheld function LPN merge which allows consolidating staged LPNs .&#x20;

**1.33.1**&#x20;

* **Added new handheld function to Adjust Out full bin/LPN without scanning product**&#x20;
* **Added ability to download most recent APK directly without Google Play Store**&#x20;
* **Added Help button with Reseller's information**&#x20;
* **Added additional information fields to pickticket detail screen to help with load planning**
* **Added additional information to packslip report** &#x20;

1.32.1

* &#x20;**Added facility to assign/unassign truck loads to pick tickets even before pick tickets are picked or allocated**
* &#x20;**Added a separate setting for handheld weight/dims from default reporting UoM**

&#x20;1.31.1 - **September 25th, 2021**

* &#x20;**Added total number of cartons to Packslip report**
* &#x20;**Cosmetic fixes to BOL report**
* &#x20;**Added facility to create Master BOL for multiple customers**
* &#x20;**Added a restriction for zone names. Now cannot create zones with the same name**
* &#x20;**Added an option to do Bulk Updates to Pick tickets and Purchase orders**
* &#x20;**Added facility to configure dimensions data to Bins/Zones**
* &#x20;**Added new handheld screens to capture dimensions and weight of Totes and LPNs**

**1.30.1**&#x20;

* **Added new handheld tag list screen to fulfillment**

1.29.1

* &#x20;**Added facility to activate and deactivate users to temporarily prohibit access to the system**&#x20;
* **Added Appointment date to pick tickets**&#x20;
* **Added Must Arrive date to pick tickets**&#x20;
* **Enabled printing tags from the pick ticket list**&#x20;
* **Made comments editable past Draft state**&#x20;
* **Surfaced comments in the pick ticket grid**&#x20;
* **Added facility to run an import over existing tenants to retain previous settings (ex: integrations or print station)**

&#x20;**1.28.1**&#x20;

* **Decoupled Email sending to improve PDT performance when emails are enabled**&#x20;
* **Improved Allocation performance on large orders**&#x20;

&#x20;**1.27.1**

* **Added facility to change allocated quantities and partially release reserved stock.**
* **Added facility to Unallocate individual lines.**
* **Carrier now propagates to Pick Ticket and Tote when shipping Truck loads.**

**1.26.1**

* **Added pick skipping to Production picking.**
* **Minor changes to component consumptions in Production when using By Recipe option.**
* **Added Handheld activity dashboard.**
* **Added facility to redirect handheld to an alternative cloud server on tenant selection.**

&#x20;**1.25.1**

* **Added facility to maintain min/max inventory per Bin for product dedicated bins.**
* **Added a way to preview handheld screen of an active user session.**

&#x20;**1.24.1**

* **Added ability to setup zone with Single Bin per Product (to support POS).**
* **Added ability to setup bins with dedicated products (to support POS).**

#### &#x20;**1.23.1**&#x20;

* **Extended support for older version of Android (Lollipop SDK v19)**
* **Added a configuration that controls whether to display Product locations on Product Move**
* **Added Skip button to Product Letdown handheld option**
* **Modified LPN Letdown to display all LPNs that are in the queue instead of just the first one**&#x20;

#### **1.22.1**

* &#x20;**Added facility to re-allocate orders that have already started being picked**&#x20;
* &#x20;**Added facility to move allocated stock (based on configuration)**&#x20;
* **Added Quantity prompt on Packsize Break down handheld function**

**1.21.1**

* **Added additional Packsize handling option to Zones/Bins. Zones/Bins could be setup to auto break Packs to Eaches**&#x20;
* **Added Letdown by product handheld function to avoid pulling down the whole pallet**

&#x20;**1.20.1**

* **Introduced new Picking mode**&#x20;
  * &#x20;Carton Picking (pick individual cartonized boxes) - Renamed former 'Carton Pick' to 'Full pack picking'
  *   Added additional allocation flavor for Packsize controlled items





