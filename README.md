SELECT id
FROM angular_darpan.case_upload_excel_basic
WHERE LOWER(district_name) = LOWER('Patna City')
  AND (
        subdivision_name LIKE '%सचिवालय %'
     OR subdivision_name LIKE '%सचिवालय-01%'
     OR subdivision_name LIKE '%सचिवालय-1%'
  );
  
  
  
  -------------------final script------------------
  SET SQL_SAFE_UPDATES = 0;

START TRANSACTION;

-- =========================
-- 1️⃣ CHILD TABLE: accused
-- =========================
DELETE FROM angular_darpan.case_upload_excel_accused
WHERE basic_id IN (
  -- 👉 yahan poori basic_id list paste karo (exact same list)
);

-- =========================
-- 2️⃣ CHILD TABLE: cp
-- =========================
DELETE FROM angular_darpan.case_upload_excel_cp
WHERE basic_id IN (
  -- 👉 yahan bhi wahi SAME basic_id list paste karo
);

-- =========================
-- 3️⃣ PARENT TABLE: basic
-- =========================
DELETE FROM angular_darpan.case_upload_excel_basic
WHERE id IN (
  -- 👉 yahan bhi wahi SAME basic_id list paste karo
);

COMMIT;

SET SQL_SAFE_UPDATES = 1;
