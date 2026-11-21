<img src="assets/logo.png" width="112" height="112" alt="Barnowl logo">

# Barnowl

Inspect a supplied audit export for sequence gaps, replays and clock reversals. This Blyx workflow framework is part of the audit, identity and reliability collection.

Sorting an export by timestamp can conceal a clock rollback. Audit receipt order and sequence continuity as separate signals. [OpenTelemetry, logs data model](https://opentelemetry.io/docs/specs/otel/logs/data-model/)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-barnowl.git
cd blyx-barnowl
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-barnowl) · [Package page](https://www.blyx-lang.space/packages/barnowl) · [Handbook](https://doc.blyx-lang.space/guide/barnowl)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-barnowl.git vendor/barnowl
```

```blyx
use vendor::barnowl::barnowl;

fn main() {
    let ids = [40, 42, 42];
    let times = [10, 14, 12];
    let result = barnowl_audit(ids, times);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
1
1
1
2
0
```

## API

`barnowl_audit(ids, times)`

Returns [gap count, nonadvancing IDs, backward clock steps, first reversed row, clean flag]. Preserve original receipt order; a gap is an observation for investigation. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| ids | Vector of values, each a nonnegative exact integer |
| times | Vector of values, each a exact signed integer |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "40,42,42" "10,14,12"
```

## Libraries

- [EventOrder](https://github.com/Rahulchaube1/blyx-eventorder/tree/v0.1.0) — Locate time-order anomalies in a log stream in receipt order.
- [AuditGaps](https://github.com/Rahulchaube1/blyx-auditgaps/tree/v0.1.0) — Count forward gaps and nonadvancing IDs in an audit export.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-barnowl/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
