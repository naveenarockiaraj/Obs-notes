
## 📋 Query Parameter Standardization - Change Plan

Based on **NEEVEDEV-6136** and **Section 4: Query Parameter Standardization** from your Confluence documentation, here's the complete breakdown of changes required:

---

## **TABLE 1: Pagination Parameters – All 16+ List Controllers**

| File | Current Param | Required Change | Why | Issue |
|------|----------------|-----------------|-----|-------|
| `endpoint_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `connection_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `user_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `org_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `site_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `portfolio_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `network_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `network_v2_controller.py` | `page=0` (0-indexed) | Change to `page=1` (1-indexed) + alias | Discovery endpoints should use 1-indexed paging | 0-indexed pagination is non-standard |
| `node_v2_controller.py` | `page=0` (0-indexed) | Change to `page=1` (1-indexed) + alias | Discovery endpoints should use 1-indexed paging | 0-indexed pagination is non-standard |
| `idp_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `firewall_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `secret_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `user_preference_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `accesslog_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `auditlog_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |
| `activity_controller.py` | `page`, `size` | Add alias for `size` → `pageSize` | Standard camelCase + snake_case support | Missing camelCase alias |

---

## **TABLE 2: Filter Parameters – All Controllers Using FilterDepends**

| File | Current Param | Required Change (Add Alias) | Why | Issue |
|------|----------------|---------------------------|-----|-------|
| All filter classes | `order_by` | `alias="sortBy"` | Google API standard: sort direction via camelCase | snake_case violates JSON API standard |
| All filter classes | `custom_search` | `alias="search"` | Standard query param naming | Non-standard name |
| All filter classes | `site_id` | `alias="siteId"` | camelCase consistency | snake_case violates JSON standard |
| All filter classes | `network_id` | `alias="networkId"` | camelCase consistency | snake_case violates JSON standard |
| All filter classes | `org_id` | `alias="orgId"` | camelCase consistency | snake_case violates JSON standard |

---

## **TABLE 3: Core Infrastructure Changes**

| File | Current State | Required Change | Why | Type |
|------|----------------|-----------------|-----|------|
| filter_utils.py | No `alias_generator` | Add `alias_generator = to_camel` to all Pydantic models | Automatic camelCase aliasing for all filter params | Critical Dependency |
| filter_utils.py | All params snake_case | Add `Field(..., alias="...")` for EVERY param | Manual alias support as fallback | Implementation Detail |
| `utopia/common/pagination.py` | Does not exist | **CREATE NEW FILE** with `PaginationParams` class | Centralized pagination dependency (DRY principle) | New Infrastructure |

---

## **TABLE 4: Pagination Parameter Details**

| Aspect | Current | Required | Notes |
|--------|---------|----------|-------|
| **Page Parameter** | `page` (int) | `page` (int, 1-indexed) | Must accept via `Query(1, ge=1)` |
| **Size Parameter** | `size` | `size` with `alias="pageSize"` | Accept BOTH `?size=10` AND `?pageSize=10` |
| **Default Size** | `10` | `25` | Align with Google API standards |
| **Max Size** | None (no constraint) | `100` | Coerce values > 100 to 100 via validation |
| **Size Constraint** | Missing | `Query(..., ge=1, le=100)` | Reject invalid sizes with 400 Bad Request |
| **Discovery Paging** | `page=0` (v2 controllers) | `page=1` (1-indexed) | Change in `network_v2_controller.py` and `node_v2_controller.py` |

---

## **TABLE 5: Affected Filters (Complex Filtering)**

| Module | Filter Class | snake_case Params Requiring Aliases | 
|--------|-------------|-------------------------------------|
| filter_utils.py | Global params | `order_by` `custom_search` `site_id` `network_id` `org_id` |
| `endpoint/` | `EndpointFilter` | Same + `ip_type` (check) |
| `node/` | `NodeFilter` | Same + `hardware_serial_number` (check) |
| `connection/` | `ConnectionFilter` | Same + `connection_type` (check) |
| All other modules | Individual filters | Inherit from global → need aliases |

---

## **TABLE 6: Implementation Scope**

| Category | Count | Files Affected | Complexity |
|----------|-------|-----------------|------------|
| List Controllers to Update | 16 | endpoint, connection, user, org, site, portfolio, network, network_v2, node_v2, idp, firewall, secret, user_preference, accesslog, auditlog, activity | Medium (add Query alias to each) |
| Filter Classes to Update | ~20 | All within `filter_utils.py` and per-module filters | Medium (add aliases) |
| Infrastructure Files | 2 | `filter_utils.py`, `pagination.py` (new) | High (new centralized dependency) |
| 0→1 Indexed Pagination | 2 | `network_v2_controller.py`, `node_v2_controller.py` | Low (change defaults) |

---

## **SUMMARY OF CHANGES**

### ✅ **What We're Changing:**

1. **Pagination params across 16+ controllers** — add `alias="pageSize"` to `size` parameter
2. **Filter parameters across all modules** — add camelCase aliases (`sortBy`, `search`, `siteId`, `networkId`, `orgId`)
3. **Discovery endpoints** — change from 0-indexed to 1-indexed pagination
4. **Core infrastructure** — create centralized `PaginationParams` dependency + update `filter_utils.py` with `alias_generator`

### 📌 **Why We're Changing:**

- **Standards Compliance**: Aligns with Google API Design Guide (AIP-132, AIP-160)
- **Consistency**: All list endpoints use same pagination interface
- **Client Experience**: Supports both snake_case (internal) and camelCase (external) aliases
- **Bug Prevention**: Fixes 0-indexed pagination bug in v2 controllers
- **DRY Principle**: Centralized pagination reduces code duplication

---

### ⏸️ **Please confirm:**

1. ✅ Do you want to proceed with these changes **in this exact order**?
2. ✅ Should I apply the `alias_generator = to_camel` approach from Pydantic v2?
3. ✅ Are you okay with **changing default `size` from 10 → 25** per Google standards?
4. ✅ Should I also add `max_size=100` validation as mentioned in the standards?

Once you confirm, I'll implement all changes systematically without modifying the code yet.