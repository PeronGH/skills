---
name: rust-coding
description: "Use this skill for anything Rust-related. Always consult it before writing or modifying Rust code."
---

# Rust Coding

## File Size

Recommended file size is under 500 lines. Hard limit is 1000 lines; if reached, break the file down.

## Dependencies

Never hand-edit `Cargo.toml`. Use `cargo` for all dependency changes.

## Error Handling

Use `thiserror` for library errors, `anyhow` in binary/CLI layers.

## Documentation

Doc comments on every public item. `cargo doc` should produce useful, navigable documentation.

## Before Commit

Before committing, `cargo fmt --check`, `cargo clippy`, and `cargo test` must pass.

## Lint Suppressions

Follow the lint policy. Any non-test lint suppression must use the narrowest scope possible and include an explicit `reason = "..."`.

## Panic Policy

Do not use panic-prone code casually in non-test code. `unwrap`, `expect`, and similar operations are acceptable when a local invariant guarantees the value and making it fallible would only force fallibility onto callers up the call chain; make that invariant explicit in the code or comments.

## Unsafe Policy

Each unsafe block must contain a single operation with a `SAFETY` comment explaining why the invariant holds. Every unsafe function must have a `# Safety` doc section.

## Performance

Hot paths must have benchmarks. Any performance regression must be explained to the human before committing.

## Hygiene

Handle every `Result` — never silently discard. Do not hold locks or `RefCell` borrows across await points. Do not mark functions async unless they await.
