# Privattice: reference workflow

Status: planned domain acceptance; the current JSON structure preview does not implement this workflow.

Import synthetic access snapshot -> bounded path query -> inspect provenance -> simulate removing edge -> rebuild graph -> verify identical source hash.

Required invariants:

- No authority only in graph
- Bounded traversal and explicit truncation
- Every edge has provenance and confidence

Required UAT:

- snapshot مجاز را وارد کن و هر مسیر را تا source/confidence دنبال کن
- گراف را حذف و از inventory بازسازی کن؛ edge-set hash برابر باشد
- graph cyclic و پرشاخه باید truncated/deadline بدهد، نه timeout نامحدود

Machine contract: tests/scenarios/clone-to-value.json. C01/C04 create and freeze the actual synthetic positive/negative fixture formats; no real secrets, user source/traffic/case data or unlicensed corpus. A clean source clone must reproduce the entire workflow with restart and restore at C30.
