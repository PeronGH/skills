---
name: rust-coding
description: "Use this skill for anything Rust-related. Always consult it before writing or modifying Rust code."
---

# Rust Coding

## Structure

Keep code modular and DRY. Recommended file size is under 500 lines. Hard limit is 1000 lines; if reached, break the file down.

## Dependencies

Never hand-edit `Cargo.toml`. Use `cargo` for all dependency changes. Prefer well-maintained crates over hand-rolling equivalent logic. Remove dependencies that constrain the design.

## Error Handling

Use `thiserror` for library errors, `anyhow` in binary/CLI layers.

## Documentation

Doc comments on every public item. `cargo doc` should produce useful, navigable documentation. When behavior or a public API changes, update the doc comments in the same commit.

## Testing

Every `#[test]` function for integration tests must have a doc comment explaining what it covers and why it exists (`Origin:` line if harvested from other projects, `Spec:` line if validated against a specification).

## Lint Suppressions

Follow the lint policy. Any non-test lint suppression must use the narrowest scope possible and include an explicit `reason = "..."`.

## Panic Policy

In non-test code, do not use constructs that can panic at runtime. When an invariant guarantees safety, make it explicit in the code.

## Unsafe Policy

Each unsafe block must contain a single operation with a `SAFETY` comment explaining why the invariant holds. Every unsafe function must have a `# Safety` doc section.

## Performance

Performance is a priority. Use crates that provide high-performance data structures or algorithms rather than hand-rolling. Hot paths must have benchmarks. Any performance regression must be explained to the human before committing.

## Hygiene

Keep visibility as tight as possible. Handle every `Result` — never silently discard. Do not hold locks or `RefCell` borrows across await points. Do not mark functions async unless they await.
