# P4 Warehouse Troubleshooting Guide

## Overview

This guide provides solutions to common issues encountered in P4 Warehouse operations. It covers system errors, configuration problems, hardware issues, and performance optimization.

{% hint style="info" %}
**Before You Begin**: Always check system status at your P4 Warehouse dashboard and ensure you're using supported browsers (Chrome, Firefox, Edge). For complete documentation, visit `https://docs.p4.software`
{% endhint %}

## Table of Contents
- [Login & Access Issues](#login--access-issues)
- [Printing Problems](#printing-problems)
- [Mobile Device (PDT) Issues](#mobile-device-pdt-issues)
- [Inventory Discrepancies](#inventory-discrepancies)
- [Order Processing Errors](#order-processing-errors)
- [Integration & API Issues](#integration--api-issues)
- [Performance Problems](#performance-problems)
- [Data & Reporting Issues](#data--reporting-issues)
- [3PL Billing Problems](#3pl-billing-problems)
- [Emergency Procedures](#emergency-procedures)

---

## Login & Access Issues

### Cannot Login to Web Interface

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| Invalid credentials error | Incorrect username/password | Verify credentials are correct, check CAPS LOCK |
| Account locked | Too many failed attempts | Contact system administrator to unlock |
| Blank screen after login | Browser compatibility | Clear cache, try different browser |
| "No warehouse assigned" | User configuration incomplete | Admin must assign default warehouse in user settings |
| Timeout errors | Session expired | Log in again, check "Remember me" if available |

### Cannot Access Specific Modules

**Check User Permissions:**
1. Navigate to `Setup > System > Users`
2. Click on the affected user
3. Review **Modules** section
4. Ensure required permissions are checked
5. Click **Update**

**Common Permission Issues:**
- Receiving module disabled → Cannot process POs
- Fulfillment module disabled → Cannot process orders
- Reports module disabled → Cannot access analytics

### PDT User Cannot Login

```
Error: "Invalid User or Password"
```

**Solutions:**
1. Verify username is lowercase (PDT is case-sensitive)
2. Check user is active in system
3. Confirm correct warehouse selected
4. Ensure PDT has internet connection
5. Verify server URL is correct in PDT settings

---

## Printing Problems

### Labels Not Printing

{% hint style="danger" %}
**Critical Check**: Ensure Print Agent is running on the Windows server. No labels will print without it.
{% endhint %}

#### Step-by-Step Diagnosis

1. **Check Print Agent Status**
   - Open Windows server/computer running Print Agent
   - Open Windows Services (services.msc)
   - Look for "P4 Print Agent" service
   - If stopped, right-click and select "Start"
   - Verify service is set to "Automatic" startup

2. **Verify Printer Configuration**
   ```
   Setup > System > Printing > Printers
   ```
   - Confirm printer shows "Online" status
   - Check correct DPI setting (203/300/600)
   - Verify label formats assigned to printer

3. **Test Print Queue**
   ```
   Setup > System > Printing > Print Queue
   ```
   - Look for stuck jobs (Status: Pending)
   - Click **Reprint** for failed jobs

4. **Check Physical Printer**
   - Power is on
   - Has labels loaded
   - Ribbon installed (if thermal transfer)
   - No error lights/messages

### Wrong Label Format Printing

**Issue**: Pick labels printing on product label stock

**Solution**:
1. Go to `Setup > System > Printing > Printers`
2. Click printer's configuration icon
3. Verify label type assignments:
   - Pick Labels → Large format printer
   - Product Labels → Small label printer
   - BOL → Letter/A4 printer

### Printer Priority Issues

**Understanding Print Priority:**
1. **User assigned printer** (highest priority)
2. **Zone assigned printer**
3. **System default printer** (lowest priority)

**To Fix:**
- Check user's printer assignment
- Verify zone printer configuration
- Set appropriate default printer

---

## Mobile Device (PDT) Issues

### Scanner Not Working

#### Zebra Devices
1. Open **DataWedge** app
2. Navigate to P4 Warehouse profile
3. Ensure **Barcode Input** is enabled
4. Check **Associated Apps** includes P4W

#### Generic Android Devices
```
P4W App Settings > Scanner Configuration
- Enable camera scanner
- Set scan timeout (3-5 seconds)
- Enable continuous scanning
```

### App Crashes or Freezes

**Immediate Actions:**
1. Force close app
2. Clear app cache:
   ```
   Settings > Apps > P4W > Storage > Clear Cache
   ```
3. Restart device
4. Update app from Google Play Store

### Cannot Scan Certain Barcodes

| Barcode Type | Common Issue | Solution |
|-------------|--------------|----------|
| Code 128 | Not enabled | Enable in DataWedge settings |
| QR Code | Camera mode | Switch to 2D scanning mode |
| Damaged label | Poor quality | Reprint label, adjust printer darkness |
| Small barcode | Resolution | Increase scanner resolution |

### Network Connection Lost

**Symptoms**: "No connection to server" errors

**Solutions:**
1. Check WiFi connection
2. Verify server URL in app settings
3. Test network:
   ```
   Settings > Network > Ping Server
   ```
4. Move closer to WiFi access point
5. Switch to different WiFi band (2.4GHz vs 5GHz)

---

## Inventory Discrepancies

### Quantity Mismatches

#### Systematic Approach

1. **Identify the Discrepancy**
   ```sql
   Reports > Inventory > Variance Report
   ```
   - Note specific SKUs affected
   - Check magnitude of variance
   - Review transaction history

2. **Common Causes & Solutions**

   | Cause | Indicator | Resolution |
   |-------|-----------|------------|
   | Receiving error | PO shows received, inventory doesn't match | Check receiving transactions, adjust if needed |
   | Allocation stuck | Available < On Hand - Allocated | Clear stuck allocations, reallocate |
   | Cycle count pending | Recent count not approved | Approve pending cycle counts |
   | Unit conversion error | Pack size confusion | Verify UOM consistency |

3. **Correction Process**
   ```
   Mobile Device > Adjustments > Adjust In/Out
   ```
   - Document reason code
   - Add detailed notes
   - Require supervisor approval

### Cannot Find Product in Bin

**Investigation Steps:**

1. **Verify Allocation Status**
   ```
   Reports > Inventory > Bin Contents
   ```
   Check if product is allocated to another order

2. **Check Multiple Locations**
   ```
   Mobile Device > Inventory > Product Location
   ```
   Product may be in multiple bins

3. **Review Recent Movements**
   ```
   Reports > Transaction History
   Filter by: SKU, Date Range, Transaction Type
   ```

4. **Physical Verification**
   - Perform spot cycle count
   - Check surrounding bins
   - Verify correct warehouse/zone

### Negative Inventory

{% hint style="warning" %}
**Critical**: Negative inventory indicates system configuration issues or process violations
{% endhint %}

**Immediate Actions:**
1. Identify affected SKUs
2. Stop shipping affected items
3. Physical count all locations
4. Adjust to actual quantities
5. Review transaction history

**Prevention:**
- Enable "Prevent Negative Inventory" in settings
- Require cycle count approval
- Implement receiving verification

---

## Order Processing Errors

### Cannot Allocate Order

**Error**: "Insufficient inventory to allocate"

**Troubleshooting:**

1. **Check Available Inventory**
   ```
   Available = On Hand - Allocated - Reserved
   ```
   
2. **Review Allocation Settings**
   - FIFO/FEFO/LIFO selection
   - Lot/Serial requirements
   - Expiry date restrictions

3. **Common Solutions:**
   - Release other orders' allocations
   - Receive pending POs
   - Move inventory from quarantine
   - Check customer's expiry allowance

### Pick Tickets Not Printing

**Checklist:**
1. ✓ Order is allocated (100%)
2. ✓ Order is waved
3. ✓ Zone printer configured
4. ✓ Pick label format assigned
5. ✓ Print Agent running

### Cannot Ship Order

**Error**: "Order not ready for shipment"

**Requirements for Shipping:**
- [ ] All items picked
- [ ] Tote/Pallet labeled
- [ ] Content label printed (if required)
- [ ] Carrier selected
- [ ] Ship-to address valid

### Backorders Not Generating

**Configuration Check:**
```
Setup > System > Configuration > Fulfillment
- Enable "Auto-generate backorders"
- Set backorder threshold
- Configure backorder numbering
```

---

## Integration & API Issues

### API Authentication Failures

**Error 401: Unauthorized**

```json
{
  "error": "Invalid API key",
  "status": 401
}
```

**Solutions:**
1. Regenerate API key in user settings
2. Verify Bearer token format:
   ```
   Authorization: Bearer YOUR_API_KEY
   ```
3. Check API key hasn't expired
4. Confirm tenant identifier is correct

### Integration Data Not Syncing

**Diagnostic Steps:**

1. **Check API Logs**
   ```
   Reports > Integration > API Log
   ```
   - Review error messages
   - Note failed endpoints
   - Check timestamp patterns

2. **Common Sync Issues:**

   | Issue | Symptom | Fix |
   |-------|---------|-----|
   | Rate limiting | 429 errors | Implement retry logic with backoff |
   | Data validation | 400 errors | Verify required fields, data types |
   | Network timeout | Connection errors | Increase timeout, check firewall |
   | Duplicate prevention | Records not updating | Include unique identifiers |

3. **Test with Minimal Payload**
   ```bash
   curl -X POST https://api.p4warehouse.com/ProductApi/CreateOrUpdate \
     -H "Authorization: Bearer YOUR_KEY" \
     -H "Content-Type: application/json" \
     -d '{"sku":"TEST001","description":"Test"}'
   ```

### Webhook Not Receiving Events

**Verification Process:**
1. Confirm webhook URL is publicly accessible
2. Check SSL certificate is valid
3. Verify endpoint returns 200 OK
4. Review webhook subscription settings
5. Test with webhook testing service

---

## Performance Problems

### System Running Slowly

#### Browser Optimization
1. Clear browser cache and cookies
2. Disable unnecessary extensions
3. Update to latest browser version
4. Close unused tabs
5. Use incognito/private mode for testing

#### Network Diagnostics
```
Command Prompt / Terminal:
ping api.p4warehouse.com
tracert api.p4warehouse.com
```

Check for:
- High latency (>200ms)
- Packet loss
- Network congestion

#### Database Performance

**For Custom Reports:**
- Add appropriate indexes
- Limit date ranges
- Use pagination
- Avoid SELECT *
- Optimize JOIN operations

### Large Reports Timing Out

**Solutions:**
1. **Break into smaller date ranges**
2. **Schedule for off-peak hours**
3. **Export in batches**
4. **Use data filters:**
   - Specific warehouse
   - Product categories
   - Customer segments

### Mobile Device Slow Response

**Optimization Steps:**
1. Reduce active applications
2. Clear P4W app cache
3. Update device firmware
4. Check WiFi signal strength
5. Disable battery optimization for P4W

---

## Data & Reporting Issues

### Reports Showing Incorrect Data

**Validation Process:**

1. **Check Report Parameters**
   - Date range selection
   - Warehouse filter
   - Status filters
   - Client selection (3PL)

2. **Verify Data Source**
   ```sql
   -- Example: Verify inventory totals
   SELECT SKU, SUM(Quantity) as Total
   FROM Inventory
   WHERE WarehouseID = @WarehouseID
   GROUP BY SKU
   ```

3. **Common Report Issues:**

   | Report Type | Common Issue | Solution |
   |------------|--------------|----------|
   | Inventory | Includes allocated | Filter by available only |
   | Shipping | Wrong date range | Use ship date, not order date |
   | Receiving | Missing POs | Include all statuses |
   | 3PL Billing | Wrong period | Check billing cycle dates |

### Cannot Export Reports

**Error**: "Export failed"

**Solutions:**
1. Reduce data set size
2. Try different export format (CSV vs Excel)
3. Check browser popup blocker
4. Increase browser timeout
5. Use scheduled reports instead

### Custom KPIs Not Updating

**Troubleshooting:**
1. Verify SQL query syntax
2. Check data source connections
3. Review refresh schedule
4. Test query in SQL editor
5. Validate column mappings

---

## 3PL Billing Problems

### Invoices Not Generating

**Requirements Checklist:**
- [ ] Client billing enabled
- [ ] Billing profiles assigned
- [ ] Billing cycle configured
- [ ] Transaction data present
- [ ] Period end date reached

**Manual Generation:**
```
3PL > Invoicing > Generate Invoice
Select Client > Select Period > Generate
```

### Incorrect Billing Amounts

**Audit Process:**

1. **Review Billing Profile**
   ```
   3PL > Billing Profiles > [Profile Name]
   ```
   - Check rate configuration
   - Verify calculation method
   - Confirm precedence order

2. **Validate Transactions**
   ```
   Reports > 3PL > Transaction Detail
   ```
   - Match quantities
   - Verify dates in period
   - Check transaction types

3. **Common Billing Errors:**

   | Error | Cause | Fix |
   |-------|-------|-----|
   | Missing charges | Profile not assigned | Assign profile to client |
   | Double billing | Duplicate profiles | Adjust precedence |
   | Wrong rates | Outdated profile | Update billing rates |
   | Period mismatch | Wrong cycle dates | Correct billing cycle |

### Email Notifications Not Sending

**Configuration Check:**
```
Setup > System > Configuration > Email
```
- SMTP server settings
- Authentication credentials
- From address
- Port and SSL/TLS settings

**Test Email:**
```
Setup > System > Configuration > Email > Test
```

---

## Emergency Procedures

### System Completely Down

**Immediate Actions:**

1. **Check Critical Services**
   - Verify Print Agent service is running (Windows Services)
   - Test network connectivity
   - Check server accessibility

2. **Notify Key Personnel**
   - IT administrator
   - P4 Warehouse support
   - Management team

3. **Implement Contingency**
   - Switch to paper pick lists
   - Manual inventory tracking
   - Queue transactions for later

### Data Recovery Needed

{% hint style="danger" %}
**STOP**: Do not attempt fixes that might worsen data loss. Contact P4 Warehouse support immediately.
{% endhint %}

**Information to Gather:**
- Last known good state time
- Recent transactions before issue
- Users affected
- Error messages
- Actions taken before problem

### Integration Complete Failure

**Fallback Procedures:**

1. **Enable Manual Mode**
   - Stop automatic imports
   - Queue outbound messages
   - Document all transactions

2. **Manual Data Entry**
   - Priority orders only
   - Batch entry when possible
   - Maintain transaction log

3. **Recovery Process**
   - Fix integration issue
   - Process queued transactions
   - Reconcile any discrepancies
   - Verify data integrity

---

## Escalation Matrix

### When to Contact Support

| Severity | Examples | Response Time | Contact Method |
|----------|----------|---------------|----------------|
| **Critical** | System down, data loss, cannot ship | 1 hour | Phone + ticket |
| **High** | Major feature broken, integration failed | 4 hours | Priority ticket |
| **Medium** | Reports incorrect, performance issues | 1 business day | Standard ticket |
| **Low** | Questions, minor bugs, enhancements | 2-3 business days | Email/ticket |

### Information to Provide

Always include:
1. **Tenant identifier**
2. **User experiencing issue**
3. **Exact error message**
4. **Steps to reproduce**
5. **Screenshot/video if applicable**
6. **Time issue occurred**
7. **Recent changes made**

### Support Contacts

- **Documentation**: `https://docs.p4.software`
- **Support Portal**: Contact your P4 Warehouse partner
- **Swagger API Documentation**: `https://api.p4warehouse.com/swagger/index.html`

---

## Preventive Maintenance

### Daily Checks
- [ ] Print Agent service running (Windows Services)
- [ ] All printers online
- [ ] No stuck allocations
- [ ] Integration logs reviewed

### Weekly Tasks
- [ ] Clear old print jobs
- [ ] Review error logs
- [ ] Check disk space
- [ ] Verify backup completion
- [ ] Restart Print Agent service if needed

### Monthly Procedures
- [ ] Update user permissions
- [ ] Review integration performance
- [ ] Clean up test data
- [ ] Update documentation
- [ ] Verify Print Agent service set to Automatic startup

---

{% hint style="success" %}
**Best Practice**: Maintain a local troubleshooting log documenting issues and solutions specific to your operation. This helps identify patterns and speeds resolution of recurring problems.
{% endhint %}