# Quick Start Guide

## Prerequisites Checklist

Before beginning your P4 Warehouse implementation, ensure you have:

- [ ] **Infrastructure Requirements**
  - [ ] Windows computer for Print Agent (always on)
  - [ ] Supported label printers (203/300/600 DPI)
  - [ ] Android devices (Lollipop+, preferably Zebra)
  - [ ] Stable internet connection
  - [ ] Modern web browser (Chrome/Firefox/Edge)

- [ ] **Business Information Ready**
  - [ ] Company structure (Single/Multi-company/3PL)
  - [ ] Warehouse layouts and zone definitions
  - [ ] Product SKUs and descriptions
  - [ ] Customer and vendor lists
  - [ ] Billing profiles (if 3PL)

## Critical Setup Sequence

{% hint style="danger" %}
**IMPORTANT**: Follow this exact sequence to avoid configuration issues. Some elements cannot be deleted once transactions exist.
{% endhint %}

### Phase 1: Foundation (Day 1)

#### 1.1 3PL/Multi-Company Setup (If Applicable)
**Path**: `Setup > 3PL > Clients`

⚠️ **This MUST be done first if using multi-company or 3PL features**

1. Click **New** button
2. Enter Company Name and SSCC ID (7-9 digits)
3. For 3PL: Enable "Billing" checkbox
4. Configure billing cycle if 3PL:
   - Monthly/Bi-weekly/Weekly
   - Set billing start date
   - Enable/disable auto-post

#### 1.2 Create Warehouse
**Path**: `Setup > System > Warehouse`

1. Click **New** button
2. Enter Warehouse Code (must match ERP if integrated)
3. Complete address information
4. Click **Update** to save

### Phase 2: Warehouse Configuration (Day 1-2)

#### 2.1 Zone Setup
**Path**: `Warehouse > Edit > Zones`

Create zones in this order:
1. **RECEIVING** - For inbound processing
2. **STAGING** - For order consolidation  
3. **SHIPPING** - For outbound
4. **PICKING** zones (A, B, C, etc.)
5. Special zones if needed:
   - **QUARANTINE** - For holds
   - **RETURNS** - For RMA processing
   - **COOLER/FREEZER** - Temperature controlled

{% hint style="info" %}
**Zone Mask Examples**:
- `A-{0:00}-{1:0}` creates: A-01-A, A-01-B, A-02-A, etc.
- `{0:00}-{1:A}-{2:00}` creates: 01-A-01, 01-A-02, 01-B-01, etc.
{% endhint %}

#### 2.2 Bin Creation
For each zone, configure bins:

1. Set zone type:
   - By Product (standard)
   - By LPN (bulk storage)
2. Configure zone mask
3. Set dimensions (critical for slotting)
4. Assign default printer

### Phase 3: Master Data (Day 2-3)

#### 3.1 Products
**Path**: `Setup > Products`

{% hint style="warning" %}
Keep SKUs under 20 characters and descriptions under 50 for optimal label printing
{% endhint %}

Required fields:
- SKU (unique identifier)
- Description
- Client (if multi-company)
- Barcode (can auto-generate)

Optional but recommended:
- Dimensions (L×W×H)
- Weight
- Pack sizes
- Lot/Serial/Expiry tracking

#### 3.2 Customers
**Path**: `Fulfillment > Setup > Customers`

1. Create customer profiles
2. Add shipping addresses
3. Set default address
4. Configure expiry allowance (default 70 days)
5. Assign cartonization profile (if applicable)

#### 3.3 Vendors
**Path**: `Purchasing > Vendors`

1. Add vendor profiles
2. Complete contact information
3. Link to client (if 3PL)

### Phase 4: System Configuration (Day 3-4)

#### 4.1 Printer Setup
**Path**: `Setup > System > Printing > Printers`

1. Install Print Agent on Windows server
2. Configure printers in Windows
3. Add printers to P4 Warehouse
4. Assign label types to printers
5. Set default printer

**Printer Priority**:
1. User assigned (highest)
2. Zone assigned
3. System default (lowest)

#### 4.2 User Creation
**Path**: `Setup > System > Users`

Create users with appropriate roles:

| Role | Permissions | Typical Tasks |
|------|------------|--------------|
| Admin | Full access | System configuration |
| Dispatcher | Web access | Order management, reporting |
| Receiver | PDT + Receiving | Inbound processing |
| Picker | PDT + Picking | Order fulfillment |
| Supervisor | Web + PDT | Floor management |

#### 4.3 Automation Settings
**Path**: `Setup > System > Configuration > Business > Fulfillment > Automation`

Configure automatic processes:
- [ ] Auto-allocation on release
- [ ] Auto-wave after allocation  
- [ ] Auto-close after shipping
- [ ] Auto-generate backorders

### Phase 5: Testing (Day 4-5)

#### 5.1 Test Receiving Flow
1. Create test Purchase Order
2. Print PO label
3. Receive with PDT
4. Verify inventory in correct bin

#### 5.2 Test Picking Flow
1. Create test Sales Order
2. Allocate inventory
3. Wave order
4. Pick with PDT
5. Ship order

#### 5.3 Test Printing
- [ ] Product labels
- [ ] Bin labels
- [ ] Pick tickets
- [ ] Packing slips
- [ ] BOL documents

### Phase 6: Go-Live Preparation (Day 5-6)

#### 6.1 Data Migration
- [ ] Import complete product catalog
- [ ] Load customer database
- [ ] Enter initial inventory counts
- [ ] Set up recurring vendors

#### 6.2 Training
- [ ] Web dispatcher training (4 hours)
- [ ] PDT user training (2 hours)
- [ ] Admin training (6 hours)
- [ ] Practice scenarios

#### 6.3 Final Checks
- [ ] All printers responding
- [ ] Integration tests passed (if applicable)
- [ ] Backup procedures documented
- [ ] Support contacts confirmed

## Common Implementation Patterns

### Small E-commerce Warehouse
- Single warehouse, 2-3 zones
- Pick ticket picking
- Small parcel shipping
- Basic cycle counting

### 3PL Operation
- Multi-client setup
- Billing profiles configured
- LPN/Pallet handling
- Advanced reporting

### Manufacturing/Distribution
- Raw material zones
- Production workflows
- Bulk storage with LPN
- Truck load shipping

## First Day Operations Checklist

### Morning Setup
- [ ] Print Agent running
- [ ] All PDT devices charged
- [ ] Printers have labels/ribbon
- [ ] Users can log in

### First Transactions
1. Receive first PO
2. Process first order
3. Complete first cycle count
4. Generate first report

## Troubleshooting Quick Reference

| Issue | Solution |
|-------|----------|
| Labels not printing | Check: Print Agent running, printer online, correct assignment |
| Can't find product | Check: Correct zone, bin scanned, allocation status |
| Login fails | Check: User active, correct warehouse, permissions set |
| Integration error | Check: API credentials, network connectivity, data format |

## Support Resources

- **Documentation**: [Your GitBook URL]
- **Video Tutorials**: [YouTube/Vimeo links]
- **Support Portal**: [Ticket system URL]
- **Emergency**: [Phone numbers by region]

## Next Steps

After completing this quick start:
1. Review advanced features
2. Configure custom reports
3. Set up integrations
4. Optimize workflows

---

{% hint style="success" %}
**Congratulations!** You've completed the P4 Warehouse Quick Start. Your system is ready for operations.
{% endhint %}