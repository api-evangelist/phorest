# Phorest (phorest)

Phorest is salon and spa business management software (scheduling, point of sale, client marketing, online booking, and reporting) used by hair, beauty, and med-spa businesses across the UK, Ireland, mainland Europe, North America, and Australia. Partner-gated access is granted to the Phorest API (also called Phorest Connect by some partners) on request - a REST, basic-authenticated API scoped per business and branch that exposes clients, appointments/bookings, staff, services, products, purchases, vouchers, and reporting data so approved developers can build custom booking flows, e-commerce integrations, call-centre lookups, and reporting tools on top of a salon's Phorest data.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/phorest/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/phorest/refs/heads/main/apis.yml)

## Access model

The Phorest API is not self-serve. Access is requested from the Phorest support/API team (`api-requests@phorest.com`), quoting the requesting business's Phorest Account Number. Once granted, requests are authenticated with HTTP Basic auth using a `global/{email}` username and an API password issued by Phorest, and are scoped to a `businessId` (and, for most resources, a `branchId`) in the URL path. There is no public self-signup developer console and no sandbox account creation flow; this repository documents the API from Phorest's public reference documentation (`developer.phorest.com`) and support articles, honestly marking endpoints that are confirmed from that public reference versus anything modeled.

## Tags

- Salon Software
- Spa Software
- Scheduling
- Point of Sale
- Business Management
- Vertical SaaS

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## APIs

### Phorest Clients API

Create, retrieve, update, and list clients (individually or in batch) scoped to a business, including filtering by email, phone, name, or update time, plus client categories used for newsletter and marketing segmentation. Confirmed against Phorest's public API reference.

- **Human URL:** [https://developer.phorest.com/reference/getclients](https://developer.phorest.com/reference/getclients)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Clients
- CRM
- Client Categories

#### Properties

- [Documentation](https://developer.phorest.com/docs/using-the-client-endpoint)
- [API Reference](https://developer.phorest.com/reference/getclients)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Appointments & Bookings API

List, retrieve, update, cancel, confirm, and check in appointments for a business branch; create, cancel, activate, and note bookings; and check real-time appointment-slot availability for a set of requested services. The backbone of Phorest's bespoke online-booking use case. Confirmed against Phorest's public API reference.

- **Human URL:** [https://developer.phorest.com/reference/getappointments](https://developer.phorest.com/reference/getappointments)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Appointments
- Bookings
- Scheduling
- Availability

#### Properties

- [Documentation](https://developer.phorest.com/docs/common-api-use-cases)
- [API Reference](https://developer.phorest.com/reference/getappointments)
- [Documentation](https://developer.phorest.com/docs/list-of-errors-seen-on-appointments-bookings-endpoints)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Staff API

List and retrieve staff (individually or in batch) per branch, read staff work time tables (rota), and create, retrieve, update, and delete staff breaks. Confirmed against Phorest's public API reference; the staff work time tables endpoint does not support pagination and always returns the full date-range result set.

- **Human URL:** [https://developer.phorest.com/reference/getstafflist](https://developer.phorest.com/reference/getstafflist)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Staff
- Rota
- Breaks
- Work Time Tables

#### Properties

- [API Reference](https://developer.phorest.com/reference/getstafflist)
- [API Reference](https://developer.phorest.com/reference/getstaffworktimetables)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Services API

List services, service categories, service packages, and service special offers for a branch, including price and duration data used to build booking flows and quotes. Confirmed against Phorest's public API reference.

- **Human URL:** [https://developer.phorest.com/reference/getservices_1](https://developer.phorest.com/reference/getservices_1)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Services
- Service Categories
- Packages
- Special Offers

#### Properties

- [API Reference](https://developer.phorest.com/reference/getservices_1)
- [API Reference](https://developer.phorest.com/reference/getservicecategories)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Products & Purchases API

List retail products with stock level, pricing, and barcode data; record purchases (appointments, products, courses, or vouchers) against a client and branch, which updates stock automatically; read inventory transactions and till balances; and perform manual stock adjustments. Used for third-party e-commerce (WooCommerce/Shopify-style) integrations. Confirmed against Phorest's public API reference. Purchase creation also emits an event onto a partner-provisioned AWS SQS queue per Phorest's sqs-sample reference project.

- **Human URL:** [https://developer.phorest.com/reference/createpurchase](https://developer.phorest.com/reference/createpurchase)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Products
- Retail
- Purchases
- Point of Sale
- Inventory

#### Properties

- [Documentation](https://support.phorest.com/hc/en-us/articles/360018547979-Integrating-3rd-Party-E-Commerce-Solutions)
- [API Reference](https://developer.phorest.com/reference/createpurchase)
- [API Reference](https://developer.phorest.com/reference/getproducts)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Vouchers & Loyalty API

Create, retrieve, list, and update the balance of gift vouchers scoped to a business, and adjust a client's loyalty points balance. Phorest does not process the voucher purchase payment itself - integrators build the purchase web experience and payment step, then write the voucher via this API. Confirmed against Phorest's public API reference.

- **Human URL:** [https://developer.phorest.com/reference/getvouchers](https://developer.phorest.com/reference/getvouchers)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Vouchers
- Gift Cards
- Loyalty
- Rewards

#### Properties

- [Documentation](https://developer.phorest.com/docs/common-api-use-cases)
- [API Reference](https://developer.phorest.com/reference/getvouchers)
- [API Reference](https://developer.phorest.com/reference/createvoucher)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Branches API

List a business's branches (locations), each branch's work time table, treatment rooms, equipment/machines, and tax rates - the reference data most other Phorest endpoints are scoped underneath. Confirmed against Phorest's public API reference.

- **Human URL:** [https://developer.phorest.com/reference/getbranches](https://developer.phorest.com/reference/getbranches)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Branches
- Locations
- Rooms
- Machines
- Tax Rates

#### Properties

- [API Reference](https://developer.phorest.com/reference/getbranches)
- [API Reference](https://developer.phorest.com/reference/getbranchworktimetable)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Phorest Reporting & Reviews API

Create and poll asynchronous CSV export jobs for raw sale-level reporting over a date range, list and retrieve client reviews for syndication to external review platforms, list sales-fee records, and read marketing leads and lead statistics. Confirmed against Phorest's public API reference.

- **Human URL:** [https://developer.phorest.com/reference/createcsvexportjob](https://developer.phorest.com/reference/createcsvexportjob)
- **Base URL:** `https://api-gateway-eu.phorest.com/third-party-api-server/api/business`

#### Tags

- Reporting
- CSV Export
- Reviews
- Leads
- Sale Fees

#### Properties

- [Documentation](https://developer.phorest.com/docs/common-api-use-cases)
- [API Reference](https://developer.phorest.com/reference/createcsvexportjob)
- [API Reference](https://developer.phorest.com/reference/getreviewlist)
- [OpenAPI](openapi/phorest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/phorest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/phorest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/phorest)
- [LinkedIn](https://www.linkedin.com/company/phorest)
- [Website](https://www.phorest.com/)
- [Documentation](https://developer.phorest.com/docs/getting-started)
- [Plans](plans/phorest-plans-pricing.yml)
- [Rate Limits](rate-limits/phorest-rate-limits.yml)
- [Fin Ops](finops/phorest-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
