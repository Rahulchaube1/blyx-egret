<img src="assets/logo.png" width="112" height="112" alt="A white egret with trailing plumes stretches its elegant neck.">

# Egret

Summarize richness, singletons and dominance in an ecological field survey. This Blyx workflow framework is part of the geospatial and scientific computing collection.

Two surveys can have the same species count and very different abundance patterns. Report diversity alongside observed richness. [scikit-bio, Simpson dominance](https://scikit.bio/docs/latest/generated/skbio.diversity.alpha.dominance.html)

## Editor extension

Install **RahulChaube.blyx-egret** to run the worked example and use the framework’s function completions in a Blyx file. Open an empty `.blyx` file, enter `blyx-egret-demo`, then choose **Blyx: Run File**. [Editor downloads](https://www.blyx-lang.space/packages/egret#editor) · [Download the extension](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-egret-0.1.0.vsix) · [Starter with framework source](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-egret-starter-0.1.0.zip)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-egret.git
cd blyx-egret
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-egret) · [Package page](https://www.blyx-lang.space/packages/egret) · [Handbook](https://doc.blyx-lang.space/guide/egret)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-egret.git vendor/egret
```

```blyx
use vendor::egret::egret;

fn main() {
    let counts = [2, 0, 2];
    let result = egret_survey(counts);
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
4
2
0
0.5
2
```

## API

`egret_survey(counts)`

Returns [individuals, observed taxa, singletons, dominance, effective taxa]. An entirely empty survey has no diversity estimate. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| counts | Vector of values, each a nonnegative exact integer |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "2,0,2"
```

## Libraries

- [Richness](https://github.com/Rahulchaube1/blyx-richness/tree/v0.1.0) — Count observed taxa and singletons from an abundance vector.
- [Dominance](https://github.com/Rahulchaube1/blyx-dominance/tree/v0.1.0) — Compute Simpson dominance and its complement from abundance counts.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-egret/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The [artwork notice](assets/NOTICE.txt) records credits for earlier editions.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
