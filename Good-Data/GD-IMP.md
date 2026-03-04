### 🧩 Task 1: **Set Up Data Pipeline from OneUI to PostgreSQL for GoodData**

**Description**:  
Create a backend process to extract the required data from OneUI (SE and SBP/TIP), and push it to the PostgreSQL database used by GoodData dashboards.

**Checklist**:

-  Identify tables and fields in OneUI DB (e.g., `rdg_session_time`, `rdg_user_name`, `connection_name`, etc.)
    
-  Build extraction logic for SE and SBP/TIP separately.
    
-  Schedule periodic jobs or use event-based triggers to keep the data updated.
    
-  Push the data to the target PostgreSQL DB used by GoodData.
    

**Complete When**:  
Required OneUI data is successfully pushed and validated in the PostgreSQL database.

---

### 🧩 Task 2: **Build/Update Dashboards in GoodData for SERA**

**Description**:  
Using the data from OneUI (in PostgreSQL), either build new SERA dashboards in GoodData or update existing ones to reflect accurate information.

**Checklist**:

-  Add missing SERA dashboards.
    
-  Ensure data mappings match required fields and calculations (e.g., active users over 30/60 days).
    
-  Use proper OneUI naming conventions and metrics.
    
-  Use new APIs if applicable.
    

**Complete When**:  
All required SERA dashboards are present in GoodData and data populates correctly.

---

### 🧩 Task 3: **Link SERA Dashboards into OneUI “Analyze” Section**

**Description**:  
Ensure that the new or updated SERA dashboards in GoodData show up in the Analyze tab of OneUI.

**Checklist**:

-  Confirm that GoodData workspaces are linked to OneUI.
    
-  Ensure that all SERA dashboards are now accessible under Analyze.
    
-  Add dashboard navigation if not auto-included.
    

**Complete When**:  
You can view SERA dashboards in OneUI under Analyze, just like TIP/SBP dashboards.

---

### 🧩 Task 4: **Update Dashboard Titles and Display Order**

**Description**:  
Make sure the naming and order of dashboards in the Analyze menu follow the new standards.

**Checklist**:

-  Rename `Active Users (Remote Access)` to `Active Users`.
    
-  Remove number prefixes from titles (e.g., “1. Overview” → “Overview”).
    
-  Ensure the correct display order: Overview comes first.
    

**Complete When**:  
All dashboards have clean names and follow the correct order in the UI.

---

### 🧩 Task 5: **Validate Data Accuracy Across Dashboards**

**Description**:  
Verify that the data shown in the dashboards matches the expected OneUI metrics.

**Checklist**:

-  Validate Active Users data (logins, user agents, location, etc.).
    
-  Validate Active Endpoint Connections data.
    
-  Confirm data integrity and parity with RA 25.04.
    

**Complete When**:  
All dashboards show correct, consistent, and reliable data.

---

### 🧩 Task 6: **Confirm Ownership and Deployment Process**

**Description**:  
Clarify who is responsible for adding/removing dashboards in GoodData and coordinate deployment if needed.

**Checklist**:

-  Sync with Antony Chiramel or Cory for GoodData ownership.
    
-  Determine if you have permission to publish dashboards or need to hand them off.
    

**Complete When**:  
Ownership and deployment plan are confirmed.