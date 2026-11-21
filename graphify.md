---
trigger: always_on
description: Consult the graphify knowledge graph at graphify-out/ for codebase and architecture questions.
---

# Graphify Strict Token-Saving Rules

1. **Baca Report, Larang Baca JSON/HTML:** HANYA baca `graphify-out/GRAPH_REPORT.md` untuk memahami struktur proyek. DILARANG membuka `graphify-out/graph.json` atau `graphify-out/graph.html` karena ukurannya sangat besar.
2. **Gunakan Query CLI:** Untuk melacak relasi fungsi secara spesifik, jalankan perintah terminal `graphify query "<kata kunci>"` daripada membaca banyak file kode sekaligus.
3. **Baca Baris Spesifik:** Saat membuka file kode sumber, gunakan rentang baris (`StartLine` - `EndLine`) berdasarkan informasi dari `GRAPH_REPORT.md`, hindari membaca keseluruhan file jika tidak diperlukan.

## graphify

This project has a graphify knowledge graph at graphify-out/.

Rules:
- For codebase or architecture questions, when `graphify-out/graph.json` exists, first run `graphify query "<question>"` (CLI) or `query_graph` (MCP). Use `graphify path "<A>" "<B>"` / `shortest_path` for relationships and `graphify explain "<concept>"` / `get_node` for focused concepts. When the answer is under a Markdown heading, `graphify section "<heading>"` / `get_section` returns that section's text, so the .md need not be opened. These return a scoped subgraph, usually much smaller than `GRAPH_REPORT.md` or raw grep output.
- If graphify-out/wiki/index.md exists, navigate it instead of reading raw files
- Read graphify-out/GRAPH_REPORT.md only for broad architecture review or when query/path/explain do not surface enough context
- After modifying code files in this session, run `graphify update .` to keep the graph current (AST-only, no API cost)