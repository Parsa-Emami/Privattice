# Privattice product requirements v0

Status: planning; application source not implemented. English-facing app/docs are the release default. See Persian assessment for commercial hypotheses.

Target user: مسئول امنیت تیم کوچک و مشاور IAM

Job to complete: نمایش مسیر دسترسی با منبع هر edge و شبیه‌سازی اصلاح

Differentiation hypothesis: snapshot analyzer قابل‌حمل و کم‌نصب برای دامنهٔ مشخص؛ provider زنده بعداً

## MVP acceptance scope

- واردسازی JSON/CSV inventory مجاز
- گراف در حافظه از snapshot نسخه‌دار
- query محدود و توضیح مسیر
- what-if حذف edge و گزارش تغییر

## Excluded until another decision

- اتصال زنده AD/cloud
- Apache AGE یا Neo4j
- continuous attack-path management
- SaaS مشترک چند سازمان

## End-to-end outcomes

1. snapshot مجاز را وارد کن و هر مسیر را تا source/confidence دنبال کن
2. گراف را حذف و از inventory بازسازی کن؛ edge-set hash برابر باشد
3. graph cyclic و پرشاخه باید truncated/deadline بدهد، نه timeout نامحدود

Functional requirements F01–F20 and nonfunctional/release requirements are mapped one-to-one in `plans/requirements.json`. Tests belong with their feature commit, not postponed until launch. Success: a clean installed selected profile performs the core task and recovers from documented failures. Public demand remains unvalidated until real trials are recorded.

## UI flow

Select/import scoped input -> validate limits and permission -> show actual processing state -> explain result and confidence -> review/triage where appropriate -> export -> recover in clean environment. Loading, empty, stale, partial, unauthorized, rejected input, timeout/cancel and permanent failure are explicit. Provide table/keyboard alternatives to canvas, charts and graph paths. No sensitive content in page telemetry.
