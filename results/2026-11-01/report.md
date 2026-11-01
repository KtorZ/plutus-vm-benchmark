# Plutus VM Benchmark Results

**Date:** 2026-11-01

## Environment
```
date: 2026-11-01T09:47:12+00:00
kernel: Linux 6.18.57
cpu: AMD EPYC-Milan Processor
cores: 16
memory: 61Gi
cpu flags (selected): hypervisor sse4_2 avx avx2 bmi2 fma sha_ni
topology: Model name AMD EPYC-Milan Processor; Thread(s) per core 2; Core(s) per socket 8; Socket(s) 1; Hypervisor vendor KVM; Virtualization type full; NUMA node(s) 1
lscpu mhz: n/a
cpufreq: none (no cpufreq driver, for example a KVM guest)
thp: enabled madvise, defrag madvise
kernel cmdline: BOOT_IMAGE=(hd0,gpt2)//kernels/ipabfanvi3crlh1zf18ss5fzh6lk1glg-linux-6.18.57-bzImage init=/nix/store/1nhkfsbcc9qy7g29vp49w4kxybwmiap0-nixos-system-bench-runner-26.05.20261020.cd4ea8d/init transparent_hugepage=madvise root=fstab loglevel=4 lsm=landlock,yama,bpf
timers: bench-selfdestruct.timer systemd-tmpfiles-clean.timer
load avg at start: 0.50 0.16 0.06
docker: 29.9.1 (linux/amd64)
docker cpus: 16
docker memory: 62786 MiB
docker run flags: --rm --cap-add SYS_NICE --network none
lanes: 3 (lane0 2,3,4,5; lane1 6,7,8,9; lane2 10,11,12,13; idle cores 14,15)
parallel: yes (up to 3 VMs at once; haskell and the drift probe run alone on lane0)
harness: 92dd521e27c490ce308a22ce2acd294f5bae7308
vm order: haskell chrysalis scalus-cek julc-java scalus-jit scalus-js blaze-v8 chrysalis-aot llvm-uplc-jit aiken-wasm aiken uplc-turbo uplc-turbo-bc plutigo plutuz
bench_quick: 0
bench_scripts: <all> (89 of 89 scripts)
bench_loops: d3,eval,check
bench_timing: normal
bench_trace: 0
host cpus: 0,1,14,15
server qualification: pass, ratio 1.093, attempt 1 of 3, nbg1; rejected: none; haskell geo ratio 1.093 <= 1.15 vs ccx43 reference (harness b0d8a22, 2026-10-22): auction_1-1 1.05, coop-6 1.12, uniswap-1 1.11
image haskell: ghcr.io/lantr-io/pvb-haskell:cf0113e362e9 ghcr.io/lantr-io/pvb-haskell@sha256:293da049bd7c65ee6e058bb0d782625f89ecf38ca8e80f6fcf3468740e503c8c
noise haskell: load avg before 1.45 0.54 0.19, steal during run 0.00 % (0 of 1474781 ticks) lane0
image chrysalis: ghcr.io/lantr-io/pvb-chrysalis:e2b8b3ae047a ghcr.io/lantr-io/pvb-chrysalis@sha256:765e67d6392301a2b977cbc3ed5d3d1481132dfab5c7346294900c8127eb278d
image scalus-cek: ghcr.io/lantr-io/pvb-scalus-cek:e518f535d996 ghcr.io/lantr-io/pvb-scalus-cek@sha256:b817c3c0b2e18a38507e3040981c48956d7129f30d0d1020c1445d898d38234f
image julc-java: ghcr.io/lantr-io/pvb-julc-java:5d99bb6a10a8 ghcr.io/lantr-io/pvb-julc-java@sha256:681c5af463f8c54960935ae618b789ff4e54fcfe57db025775cbd5c75edadeaa
noise julc-java: load avg before 1.20 1.05 0.76, steal during run 0.00 % (0 of 13200283 ticks) lane2
image scalus-jit: ghcr.io/lantr-io/pvb-scalus-jit:1aca35514d4c ghcr.io/lantr-io/pvb-scalus-jit@sha256:4a192b7e735b7b8ffed9ec96cff07113ad7de7282621252efbe011d7dc5ebd7b
noise scalus-cek: load avg before 1.20 1.05 0.76, steal during run 0.00 % (0 of 13293390 ticks) lane1
image scalus-js: ghcr.io/lantr-io/pvb-scalus-js:9e63edfb374a ghcr.io/lantr-io/pvb-scalus-js@sha256:4eb32b92df051e2d3116e7e43fd10f4c522c2f28534df82e7ef7c1efddb431d4
noise scalus-js: load avg before 3.58 3.39 3.31, steal during run 0.00 % (0 of 6563150 ticks) lane1
image blaze-v8: ghcr.io/lantr-io/pvb-blaze-v8:c743ca940f93 ghcr.io/lantr-io/pvb-blaze-v8@sha256:3ba639f3d830d8e94d4d89eb945f38fdd382a7503352ed5882e2eec7c2925b84
noise chrysalis: load avg before 1.04 1.01 0.75, steal during run 0.00 % (0 of 22037482 ticks) lane0
image chrysalis-aot: ghcr.io/lantr-io/pvb-chrysalis-aot:0b6b2579dcee ghcr.io/lantr-io/pvb-chrysalis-aot@sha256:5ddb9793c4e53f6b32bf6c3a8b9e6d4ade92efc0cc9bfedfd38634c76d5cbe4d
noise scalus-jit: load avg before 3.19 3.30 3.28, steal during run 0.00 % (0 of 8835563 ticks) lane2
image llvm-uplc-jit: ghcr.io/lantr-io/pvb-llvm-uplc-jit:4f3d33826b1d ghcr.io/lantr-io/pvb-llvm-uplc-jit@sha256:af55d767e44000db5ce5848545fe8f4833b0aac7b65dde84cdbbaa23cfc4b3ba
noise llvm-uplc-jit: load avg before 3.10 3.18 3.34, steal during run 0.00 % (0 of 3647281 ticks) lane2
image aiken-wasm: ghcr.io/lantr-io/pvb-aiken-wasm:0770cbcc5dd3 ghcr.io/lantr-io/pvb-aiken-wasm@sha256:8251a1aae91e85e8add5850bff0be3ad6bab70c681f38e22b721b019a4ea86df
noise blaze-v8: load avg before 3.63 3.55 3.54, steal during run 0.00 % (0 of 6059988 ticks) lane1
image aiken: ghcr.io/lantr-io/pvb-aiken:553af555815c ghcr.io/lantr-io/pvb-aiken@sha256:b1328c3825f56f452b1f7de6b156b45729d56979ab8afb122e9223fad02a5660
noise chrysalis-aot: load avg before 3.10 3.18 3.34, steal during run 0.00 % (0 of 5246715 ticks) lane0
image uplc-turbo: ghcr.io/lantr-io/pvb-uplc-turbo:c621f09f097e ghcr.io/lantr-io/pvb-uplc-turbo@sha256:83c2af47530f4dccd69d10ed4cbc16aaf05b0385b26b3e8126061f3e89befea4
noise aiken-wasm: load avg before 3.01 3.00 3.00, steal during run 0.00 % (0 of 3019561 ticks) lane2
image uplc-turbo-bc: ghcr.io/lantr-io/pvb-uplc-turbo-bc:04b6cc170f17 ghcr.io/lantr-io/pvb-uplc-turbo-bc@sha256:97678a9fa315fd3b9c935237f85ac0dbf551d6a1b3b8f4f7cfaad876448e6133
noise aiken: load avg before 3.00 3.00 3.00, steal during run 0.00 % (0 of 2982899 ticks) lane1
image plutigo: ghcr.io/lantr-io/pvb-plutigo:0a65c40b7b5a ghcr.io/lantr-io/pvb-plutigo@sha256:b2a909cd25fc016c543bb66f7bd4355543ceea981ed1c9cfcc51cfd9bdff8e4f
noise uplc-turbo: load avg before 3.33 3.13 3.03, steal during run 0.00 % (0 of 3016455 ticks) lane0
image plutuz: ghcr.io/lantr-io/pvb-plutuz:78e70bdbc120 ghcr.io/lantr-io/pvb-plutuz@sha256:3f145d66b434529cc15320f0081ee9c12b177c5bd9eceb1a141f44ce6da8d1af
noise plutigo: load avg before 3.12 3.16 3.09, steal during run 0.00 % (0 of 1698100 ticks) lane1
noise uplc-turbo-bc: load avg before 3.08 3.14 3.08, steal during run 0.00 % (0 of 2914420 ticks) lane2
noise plutuz: load avg before 3.13 3.16 3.12, steal during run 0.00 % (0 of 1428985 ticks) lane0
steal during the whole run: 0.00 % (0 of 33332356 ticks)
load avg at end: 1.20 1.87 2.44
drift (haskell, end vs start): +0.0 % over 5 scripts
```

*The 89 scripts are PlutusV1-era programs. Every VM evaluates them as PlutusV3 programs at protocol version 11 with the mainnet cost model, like Plutus's own `validation` CEK benchmark; the node would run them as PlutusV1.*

*Drift (Haskell, end vs start): +0.0 % over 5 scripts. The run timed Haskell again at its end; this is the change of its time.*

## Summary (geometric mean across all scripts)

*Note: VMs that fail or skip a script are assigned the slowest competitor's time for that script.*
*A compiling VM's timed loop runs the compiled script ("decode and compile excluded": the decode and the compile run once per script, before timing). So it has only an eval-only time: its Geo Mean (decode + eval) is "–" and it is not ranked. The Compile column is the geometric mean of the compile time over the scripts.*
*Geo Mean: flat decode + evaluation (the ranking). Eval only: evaluation of a program decoded before the timed loop, geometric mean over its scripts.*
*Aiken WASM caches decoded programs inside the library, so its time is shown as eval only. It is not in the decode + eval ranking; it is ranked on eval only (Geo Mean "–").*
*Aiken uplc WASM (Rust → WASM / Node V8), "decode cached (by the library)": The library caches the decoded program by a hash of the flat bytes. After the first call (in the warm-up), the timed loop runs hash + evaluation, without the decode. Its eval-only time is the same loop.*

| VM | Language | Geo Mean | vs Fastest | Eval only | Compile | Check |
|---|---|---|---|---|---|---|
| **Scalus CEK (Scala / JVM)** | Scala / JVM | 269.11 us | 1.00x | 169.33 us | - | pass |
| **Plutigo (Go)** | Go | 381.48 us | 1.42x | 272.56 us | - | pass |
| **amaru-uplc (Rust)** | Rust | 426.51 us | 1.58x | 324.54 us | - | pass |
| **plutus-core (Haskell / GHC)** | Haskell / GHC | 713.87 us | 2.65x | 275.12 us | - | pass |
| **Scalus.js CEK (Scala.js / Node V8)** | Scala.js / Node V8 | 1.44 ms | 5.34x | 970.44 us | - | pass |
| **Aiken uplc (Rust)** | Rust | 8.15 ms | 30.29x | 6.16 ms | - | pass |
| **Aiken uplc WASM (Rust → WASM / Node V8)** (decode cached (by the library)) | Rust → WASM / Node V8 | – | eval only | 887.88 us | - | pass |

### Experimental

Run, gated and shown, but not ranked: not in the table above, not a competitor in the penalty rule. Geo Mean uses the penalty rule against the ranked VMs. Geo Mean "–" (compiled once before timing, see the compile column): the VM has only an eval-only time.

| VM | Language | Geo Mean | Eval only | Compile | Check | Reason |
|---|---|---|---|---|---|---|
| **Scalus JIT (Scala / JVM)** | Scala / JVM | – | 91.77 us | 1.72 s (decode and compile excluded) | pass | **no downstream user**. not ranked: the JIT module is published (Maven, since Scalus 1.4.1) but has no downstream users yet (spec D17) |
| **blaze-plutus (TypeScript / Node V8)** | TypeScript / Node V8 | 1.25 ms | 1.03 ms | - | pass | **no downstream user**. not ranked: no released project outside the Blaze repo depends on @blaze-cardano/plutus yet; Blaze itself evaluates scripts with @blaze-cardano/vm (Aiken uplc as WASM) (spec D17) |
| **Chrysalis (C# / .NET JIT)** | C# / .NET JIT | 539.52 us | 402.80 us | - | pass | **pre-release only**. not ranked: only pre-releases on NuGet (Chrysalis.Plutus -alpha); the one stable version, 1.7.1, is unlisted (spec D22) |
| **Chrysalis AOT (C# / .NET AOT)** | C# / .NET AOT | 580.14 us | 443.74 us | - | pass | **pre-release only**. not ranked: only pre-releases on NuGet (Chrysalis.Plutus -alpha); the one stable version, 1.7.1, is unlisted (spec D22) |
| **Julc Java CEK (Java / JVM)** | Java / JVM | 485.73 us | 394.16 us | - | pass | **pre-release only**. not ranked: only pre-releases (0.1.0-preNN), and no downstream users yet (spec D22) |
| **Plutuz (Zig)** | Zig | 519.35 us | 338.75 us | - | pass | **no release**. not ranked: no release (no tags or releases on GitHub), pinned to a main commit (spec D22) |
| **llvm-uplc JIT (C++ / LLVM)** | C++ / LLVM | – | 110.84 us | 8.13 s (decode and compile excluded) | outdated cost model | **outdated**. not ranked: outdated. Its built-in cost model is variant C (before protocol version 11; divideInteger c11 549, mainnet 960), no API takes a cost model, and its last commit is from 2026-04-16. No release (spec D22) |
| **amaru-uplc BC (fork) (Rust)** | Rust | 339.29 us | 220.06 us | - | pass | **no release**. not ranked: no release has the bytecode mode; it is in the fork jonathanlim222/uplc (closed PR pragma-org/uplc#47), pinned to a commit (spec D22) |

### Notes

- **Aiken uplc (Rust)**: Aiken v1.1.24 copies the CEK environment on every lambda application (quadratic in recursion depth). aiken main fixes it (PRs [#1451](https://github.com/aiken-lang/aiken/pull/1451), [#1452](https://github.com/aiken-lang/aiken/pull/1452): coop-6 92 ms -> 1.2 ms), but no release contains the fix yet.
- **Aiken uplc WASM (Rust → WASM / Node V8)**: Built from [colll78/aiken](https://github.com/colll78/aiken) (aiken main plus fixes), which includes the CEK fixes that v1.1.24 lacks.

### History (speed relative to Haskell plutus-core, same run; higher is faster)

| VM | 2026-10-23 | 2026-10-26 | 2026-10-27 | 2026-11-01 | Change vs previous run |
|---|---|---|---|---|---|
| plutus-core (Haskell / GHC) | 1x (Haskell) | 1x (Haskell) | 1x (Haskell) | 1x (Haskell) | reference |
| Scalus JIT (Scala / JVM) (experimental, eval only) | 2.2x faster | 2.6x faster | 2.9x faster | 3.0x faster | no change (within ±5 % noise) |
| Scalus CEK (Scala / JVM) | 1.8x faster | 3.0x faster | 2.6x faster | 2.7x faster | no change (within ±5 % noise) |
| Scalus.js CEK (Scala.js / Node V8) | 5.0x slower | 2.1x slower | 2.1x slower | 2.0x slower | no change (within ±5 % noise) |
| Aiken uplc (Rust) | 11.6x slower | 10.2x slower | 11.6x slower | 11.4x slower | no change (within ±5 % noise) |
| Aiken uplc WASM (Rust → WASM / Node V8) (eval only) | 3.3x slower | 3.2x slower | 3.2x slower | 3.2x slower | no change (within ±5 % noise) |
| amaru-uplc (Rust) | 1.5x faster | 1.5x faster | 1.5x faster | 1.7x faster | +10 % |
| Plutigo (Go) | 2.5x faster | 2.6x faster | 2.3x faster | 1.9x faster | -19 % |
| blaze-plutus (TypeScript / Node V8) (experimental) | 2.5x slower | 2.1x slower | 1.8x slower | 1.8x slower | no change (within ±5 % noise) |
| Chrysalis (C# / .NET JIT) (experimental) | - | - | 1.3x faster | 1.3x faster | no change (within ±5 % noise) |
| Chrysalis AOT (C# / .NET AOT) (experimental) | - | - | 1.2x faster | 1.2x faster | no change (within ±5 % noise) |
| Julc Java CEK (Java / JVM) (experimental) | - | - | 1.5x faster | 1.5x faster | no change (within ±5 % noise) |
| Plutuz (Zig) (experimental) | - | - | 1.4x faster | 1.4x faster | no change (within ±5 % noise) |
| llvm-uplc JIT (C++ / LLVM) (experimental, eval only) | - | - | 2.5x faster | 2.5x faster | no change (within ±5 % noise) |
| amaru-uplc BC (fork) (Rust) (experimental) | - | - | 2.1x faster | 2.1x faster | no change (within ±5 % noise) |

A VM marked "eval only" has no decode + eval time (it compiles each script before timing, or its library caches the decode): its ratio is its eval-only time divided by Haskell's eval-only time.

Servers of the same type differ: ratios to Haskell move up to about 5 % between two runs on different servers, so a change under 5 % is shown as no change.

### Script Coverage

| VM | Passed | Failed | Missing | Total |
|---|---|---|---|---|
| Scalus CEK (Scala / JVM) | 89 | 0 | 0 | 89 |
| Plutigo (Go) | 89 | 0 | 0 | 89 |
| amaru-uplc (Rust) | 89 | 0 | 0 | 89 |
| plutus-core (Haskell / GHC) | 89 | 0 | 0 | 89 |
| Scalus.js CEK (Scala.js / Node V8) | 89 | 0 | 0 | 89 |
| Aiken uplc (Rust) | 89 | 0 | 0 | 89 |
| Aiken uplc WASM (Rust → WASM / Node V8) | 89 | 0 | 0 | 89 |
| Scalus JIT (Scala / JVM) (experimental) | 89 | 0 | 0 | 89 |
| blaze-plutus (TypeScript / Node V8) (experimental) | 89 | 0 | 0 | 89 |
| Chrysalis (C# / .NET JIT) (experimental) | 89 | 0 | 0 | 89 |
| Chrysalis AOT (C# / .NET AOT) (experimental) | 89 | 0 | 0 | 89 |
| Julc Java CEK (Java / JVM) (experimental) | 89 | 0 | 0 | 89 |
| Plutuz (Zig) (experimental) | 89 | 0 | 0 | 89 |
| llvm-uplc JIT (C++ / LLVM) (experimental) | 89 | 0 | 0 | 89 |
| amaru-uplc BC (fork) (Rust) (experimental) | 89 | 0 | 0 | 89 |

## Per-Script Results

| Script | plutus-core (Haskell / GHC) | plutus-core (Haskell / GHC) (eval only) | Scalus CEK (Scala / JVM) | Scalus CEK (Scala / JVM) (eval only) | Scalus.js CEK (Scala.js / Node V8) | Scalus.js CEK (Scala.js / Node V8) (eval only) | Aiken uplc (Rust) | Aiken uplc (Rust) (eval only) | Aiken uplc WASM (Rust → WASM / Node V8) (eval only) | amaru-uplc (Rust) | amaru-uplc (Rust) (eval only) | Plutigo (Go) | Plutigo (Go) (eval only) | Scalus JIT (Scala / JVM) (experimental) (eval only) | blaze-plutus (TypeScript / Node V8) (experimental) | blaze-plutus (TypeScript / Node V8) (experimental) (eval only) | Chrysalis (C# / .NET JIT) (experimental) | Chrysalis (C# / .NET JIT) (experimental) (eval only) | Chrysalis AOT (C# / .NET AOT) (experimental) | Chrysalis AOT (C# / .NET AOT) (experimental) (eval only) | Julc Java CEK (Java / JVM) (experimental) | Julc Java CEK (Java / JVM) (experimental) (eval only) | Plutuz (Zig) (experimental) | Plutuz (Zig) (experimental) (eval only) | llvm-uplc JIT (C++ / LLVM) (experimental) (eval only) | amaru-uplc BC (fork) (Rust) (experimental) | amaru-uplc BC (fork) (Rust) (experimental) (eval only) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| auction_1-1 | 378.71 us | 129.02 us | **155.42 us** | 74.72 us | 688.72 us | 412.91 us | 3.07 ms | 2.02 ms | 360.99 us | 211.18 us | 148.39 us | 180.06 us | 122.60 us | 28.34 us | 575.18 us | 466.41 us | 254.03 us | 173.80 us | 274.72 us | 196.54 us | 239.42 us | 181.36 us | 262.35 us | 157.20 us | 43.97 us | 167.89 us | 102.93 us |
| auction_1-2 | 1.09 ms | 422.63 us | **429.51 us** | 270.60 us | 2.07 ms | 1.40 ms | 12.28 ms | 9.90 ms | 2.62 ms | 722.03 us | 577.85 us | 575.09 us | 419.69 us | 185.49 us | 1.89 ms | 1.56 ms | 928.09 us | 716.60 us | 1.01 ms | 790.50 us | 764.59 us | 658.38 us | 838.50 us | 564.49 us | 198.73 us | 525.51 us | 356.92 us |
| auction_1-3 | 1.12 ms | 432.65 us | **425.65 us** | 273.50 us | 2.09 ms | 1.39 ms | 12.15 ms | 9.61 ms | 1.58 ms | 717.31 us | 570.08 us | 558.63 us | 405.42 us | 168.17 us | 1.86 ms | 1.48 ms | 921.02 us | 774.57 us | 1.00 ms | 802.72 us | 758.73 us | 649.59 us | 807.79 us | 540.22 us | 194.69 us | 530.26 us | 352.94 us |
| auction_1-4 | 429.45 us | 167.45 us | **148.20 us** | 93.58 us | 812.37 us | 538.95 us | 3.50 ms | 2.48 ms | 462.07 us | 249.46 us | 187.44 us | 209.52 us | 149.29 us | 34.45 us | 707.07 us | 601.89 us | 296.51 us | 217.58 us | 320.87 us | 243.75 us | 298.71 us | 233.68 us | 307.97 us | 202.48 us | 57.53 us | 202.57 us | 133.48 us |
| auction_2-1 | 377.55 us | 129.88 us | **125.39 us** | 72.64 us | 675.61 us | 411.40 us | 3.02 ms | 1.93 ms | 362.05 us | 210.69 us | 147.20 us | 180.16 us | 122.34 us | 29.09 us | 578.50 us | 469.91 us | 252.13 us | 173.21 us | 273.81 us | 196.90 us | 226.81 us | 181.16 us | 262.79 us | 157.12 us | 43.74 us | 173.20 us | 102.36 us |
| auction_2-2 | 1.09 ms | 430.72 us | **429.53 us** | 268.87 us | 2.05 ms | 1.40 ms | 12.53 ms | 9.80 ms | 1.56 ms | 714.73 us | 571.15 us | 581.94 us | 417.78 us | 180.82 us | 1.82 ms | 1.49 ms | 933.00 us | 726.78 us | 1.00 ms | 800.28 us | 764.34 us | 645.14 us | 830.90 us | 564.30 us | 195.97 us | 523.26 us | 354.54 us |
| auction_2-3 | 1.26 ms | 536.69 us | **539.74 us** | 362.00 us | 2.48 ms | 1.80 ms | 15.32 ms | 12.61 ms | 2.04 ms | 889.24 us | 738.34 us | 664.36 us | 508.08 us | 225.21 us | 2.37 ms | 2.00 ms | 1.18 ms | 970.53 us | 1.27 ms | 1.07 ms | 958.22 us | 819.94 us | 990.49 us | 715.42 us | 253.30 us | 644.35 us | 459.16 us |
| auction_2-4 | 1.12 ms | 436.72 us | **435.18 us** | 266.34 us | 2.11 ms | 1.38 ms | 12.40 ms | 9.66 ms | 1.57 ms | 719.86 us | 567.47 us | 560.29 us | 408.42 us | 170.54 us | 1.86 ms | 1.50 ms | 940.63 us | 730.56 us | 1.01 ms | 800.49 us | 762.49 us | 644.84 us | 810.34 us | 543.87 us | 195.47 us | 525.48 us | 352.39 us |
| auction_2-5 | 431.54 us | 168.30 us | **149.48 us** | 94.52 us | 821.73 us | 530.78 us | 3.48 ms | 2.43 ms | 463.30 us | 250.06 us | 188.75 us | 206.82 us | 145.75 us | 34.08 us | 718.00 us | 597.94 us | 302.44 us | 218.64 us | 318.51 us | 247.73 us | 294.67 us | 234.29 us | 317.88 us | 253.81 us | 59.66 us | 204.06 us | 134.67 us |
| coop-1 | 342.19 us | 178.76 us | **141.41 us** | 109.09 us | 886.26 us | 695.34 us | 5.32 ms | 4.54 ms | 413.46 us | 210.88 us | 170.62 us | 190.63 us | 143.70 us | 35.21 us | 764.17 us | 664.33 us | 250.76 us | 202.96 us | 277.13 us | 224.07 us | 296.50 us | 229.20 us | 250.48 us | 188.06 us | 63.66 us | 173.64 us | 127.31 us |
| coop-2 | 980.76 us | 566.38 us | **440.38 us** | 346.75 us | 2.63 ms | 2.29 ms | 114.16 ms | 119.23 ms | 1.47 ms | 613.27 us | 515.61 us | 730.01 us | 465.65 us | 137.96 us | 2.51 ms | 2.21 ms | 806.47 us | 658.12 us | 823.71 us | 676.71 us | 863.45 us | 730.28 us | 722.77 us | 573.54 us | 213.24 us | 518.80 us | 404.50 us |
| coop-3 | 2.18 ms | 1.65 ms | **1.28 ms** | 1.16 ms | 7.98 ms | 7.80 ms | 146.07 ms | 149.77 ms | 5.65 ms | 1.69 ms | 1.60 ms | 1.39 ms | 1.28 ms | 534.29 us | 6.04 ms | 5.88 ms | 2.61 ms | 2.38 ms | 2.82 ms | 2.54 ms | 2.31 ms | 2.15 ms | 1.81 ms | 1.65 ms | 759.84 us | 1.46 ms | 1.34 ms |
| coop-4 | 1.22 ms | 695.72 us | **551.55 us** | 444.85 us | 3.31 ms | 2.83 ms | 116.21 ms | 117.49 ms | 2.01 ms | 751.98 us | 643.17 us | 730.02 us | 530.82 us | 204.00 us | 2.98 ms | 2.58 ms | 997.75 us | 834.19 us | 1.08 ms | 906.10 us | 1.04 ms | 870.34 us | 854.28 us | 691.75 us | 286.29 us | 646.09 us | 521.10 us |
| coop-5 | 698.17 us | 307.85 us | **273.77 us** | 188.84 us | 1.52 ms | 1.20 ms | 25.65 ms | 24.57 ms | 838.38 us | 382.75 us | 285.17 us | 378.55 us | 253.30 us | 74.48 us | 1.37 ms | 1.14 ms | 494.88 us | 359.41 us | 519.77 us | 396.81 us | 534.58 us | 413.13 us | 465.65 us | 311.84 us | 117.44 us | 345.16 us | 221.32 us |
| coop-6 | 792.01 us | 532.40 us | **394.47 us** | 331.42 us | 2.40 ms | 2.10 ms | 156.09 ms | 162.29 ms | 1.25 ms | 540.82 us | 480.42 us | 670.18 us | 420.01 us | 131.19 us | 2.28 ms | 2.16 ms | 686.60 us | 606.52 us | 753.80 us | 635.69 us | 790.68 us | 673.49 us | 629.98 us | 537.61 us | 191.33 us | 451.44 us | 374.23 us |
| coop-7 | 451.04 us | 254.10 us | **209.00 us** | 158.10 us | 1.18 ms | 984.66 us | 6.50 ms | 5.62 ms | 635.08 us | 281.42 us | 233.19 us | 286.84 us | 199.80 us | 47.16 us | 1.06 ms | 936.32 us | 343.78 us | 274.06 us | 367.47 us | 305.91 us | 401.10 us | 344.77 us | 341.42 us | 261.89 us | 88.54 us | 231.67 us | 178.10 us |
| crowdfunding-success-1 | 476.72 us | 155.50 us | **151.30 us** | 85.14 us | 800.34 us | 480.28 us | 3.54 ms | 2.24 ms | 470.40 us | 230.54 us | 161.79 us | 207.75 us | 142.06 us | 31.55 us | 634.02 us | 508.29 us | 283.76 us | 193.47 us | 309.21 us | 215.76 us | 255.34 us | 206.39 us | 299.79 us | 174.02 us | 53.50 us | 199.17 us | 118.08 us |
| crowdfunding-success-2 | 480.59 us | 158.03 us | **154.66 us** | 85.50 us | 800.73 us | 474.91 us | 3.53 ms | 2.24 ms | 498.18 us | 232.94 us | 162.64 us | 212.26 us | 139.55 us | 31.73 us | 651.77 us | 527.41 us | 286.49 us | 193.11 us | 298.47 us | 213.44 us | 270.61 us | 205.23 us | 300.87 us | 173.90 us | 54.60 us | 199.98 us | 119.02 us |
| crowdfunding-success-3 | 466.08 us | 157.44 us | **156.51 us** | 86.54 us | 793.71 us | 475.85 us | 3.52 ms | 2.29 ms | 470.58 us | 234.05 us | 162.43 us | 206.37 us | 142.33 us | 32.16 us | 655.75 us | 528.67 us | 288.59 us | 192.63 us | 293.55 us | 206.38 us | 269.26 us | 206.95 us | 301.39 us | 174.25 us | 53.30 us | 197.93 us | 120.15 us |
| currency-1 | 480.85 us | 174.40 us | **173.97 us** | 109.09 us | 881.17 us | 565.22 us | 4.39 ms | 3.27 ms | 598.81 us | 284.87 us | 213.59 us | 242.69 us | 169.58 us | 53.80 us | 736.60 us | 659.89 us | 366.05 us | 272.33 us | 386.82 us | 300.38 us | 299.78 us | 247.31 us | 340.08 us | 209.44 us | 69.39 us | 223.81 us | 142.35 us |
| escrow-redeem_1-1 | 667.03 us | 249.50 us | **243.30 us** | 148.08 us | 1.20 ms | 766.03 us | 6.02 ms | 4.44 ms | 803.60 us | 383.80 us | 288.89 us | 326.84 us | 229.33 us | 68.01 us | 990.21 us | 806.56 us | 481.66 us | 365.86 us | 527.20 us | 392.32 us | 412.36 us | 332.61 us | 458.30 us | 287.17 us | 94.62 us | 302.06 us | 194.93 us |
| escrow-redeem_1-2 | 661.47 us | 247.62 us | **236.28 us** | 150.72 us | 1.20 ms | 786.68 us | 5.47 ms | 3.88 ms | 776.19 us | 384.69 us | 289.09 us | 320.77 us | 221.95 us | 67.95 us | 1.01 ms | 834.01 us | 481.63 us | 361.90 us | 515.75 us | 390.22 us | 401.58 us | 338.21 us | 455.35 us | 290.30 us | 92.48 us | 307.60 us | 193.47 us |
| escrow-redeem_2-1 | 703.08 us | 287.45 us | **264.74 us** | 176.42 us | 1.35 ms | 894.99 us | 6.90 ms | 5.22 ms | 1.01 ms | 428.16 us | 333.72 us | 361.67 us | 256.72 us | 82.07 us | 1.13 ms | 942.72 us | 562.57 us | 424.79 us | 601.81 us | 467.65 us | 473.10 us | 387.67 us | 503.91 us | 333.59 us | 115.84 us | 335.52 us | 227.07 us |
| escrow-redeem_2-2 | 721.68 us | 285.68 us | **261.47 us** | 194.03 us | 1.33 ms | 957.59 us | 6.81 ms | 5.32 ms | 974.55 us | 431.77 us | 341.19 us | 346.20 us | 256.73 us | 85.12 us | 1.14 ms | 935.71 us | 542.53 us | 418.01 us | 581.79 us | 471.03 us | 456.22 us | 384.95 us | 502.80 us | 337.34 us | 115.42 us | 338.14 us | 224.60 us |
| escrow-redeem_2-3 | 709.71 us | 285.29 us | **263.68 us** | 176.22 us | 1.35 ms | 911.95 us | 6.90 ms | 5.29 ms | 1.03 ms | 428.95 us | 336.00 us | 363.68 us | 256.79 us | 82.68 us | 1.12 ms | 947.78 us | 551.30 us | 424.23 us | 605.51 us | 466.28 us | 467.20 us | 394.88 us | 504.13 us | 334.20 us | 114.78 us | 339.29 us | 225.45 us |
| escrow-refund-1 | 507.37 us | 120.35 us | **141.63 us** | 64.90 us | 755.79 us | 366.58 us | 3.45 ms | 1.72 ms | 365.29 us | 214.88 us | 122.88 us | 216.00 us | 122.48 us | 25.00 us | 559.73 us | 386.93 us | 259.25 us | 148.28 us | 277.48 us | 155.32 us | 232.78 us | 166.68 us | 295.98 us | 131.07 us | 38.09 us | 191.76 us | 87.38 us |
| future-increase-margin-1 | 479.42 us | 174.15 us | **172.76 us** | 107.86 us | 894.45 us | 578.10 us | 4.46 ms | 3.18 ms | 599.04 us | 283.81 us | 213.38 us | 236.92 us | 164.61 us | 53.87 us | 747.44 us | 616.46 us | 370.47 us | 275.04 us | 389.29 us | 309.86 us | 308.13 us | 243.36 us | 341.38 us | 212.20 us | 68.24 us | 223.91 us | 140.94 us |
| future-increase-margin-2 | 805.52 us | 377.86 us | **324.33 us** | 238.11 us | 1.64 ms | 1.19 ms | 8.78 ms | 7.29 ms | 1.28 ms | 544.77 us | 450.79 us | 420.89 us | 323.68 us | 114.13 us | 1.46 ms | 1.30 ms | 706.17 us | 568.28 us | 762.47 us | 651.22 us | 597.38 us | 508.71 us | 609.46 us | 436.89 us | 155.56 us | 416.33 us | 298.89 us |
| future-increase-margin-3 | 815.55 us | 385.14 us | **329.53 us** | 246.50 us | 1.67 ms | 1.22 ms | 8.66 ms | 7.52 ms | 1.27 ms | 540.07 us | 446.92 us | 419.89 us | 337.24 us | 112.71 us | 1.45 ms | 1.24 ms | 688.74 us | 573.85 us | 766.94 us | 645.27 us | 595.70 us | 501.17 us | 612.77 us | 437.21 us | 156.20 us | 414.59 us | 297.47 us |
| future-increase-margin-4 | 1.19 ms | 336.24 us | **379.16 us** | 208.83 us | 1.90 ms | 1.06 ms | 10.57 ms | 7.45 ms | 1.22 ms | 630.67 us | 452.84 us | 550.39 us | 368.86 us | 155.40 us | 1.61 ms | 1.19 ms | 800.26 us | 560.13 us | 867.01 us | 620.29 us | 681.54 us | 534.74 us | 787.42 us | 461.14 us | 149.63 us | 479.28 us | 276.60 us |
| future-increase-margin-5 | 1.50 ms | 563.09 us | **590.57 us** | 372.67 us | 3.94 ms | 3.07 ms | 15.65 ms | 12.80 ms | 2.13 ms | 942.79 us | 769.99 us | 677.06 us | 506.32 us | 310.65 us | 3.75 ms | 3.28 ms | 1.27 ms | 989.10 us | 1.37 ms | 1.09 ms | 1.03 ms | 894.01 us | 1.24 ms | 912.17 us | 288.41 us | 690.35 us | 485.30 us |
| future-pay-out-1 | 479.71 us | 173.95 us | **175.50 us** | 108.61 us | 882.27 us | 574.81 us | 4.44 ms | 3.26 ms | 596.50 us | 284.63 us | 213.73 us | 243.52 us | 171.36 us | 54.77 us | 727.05 us | 588.79 us | 361.42 us | 274.94 us | 387.81 us | 296.52 us | 306.07 us | 246.97 us | 335.53 us | 212.15 us | 66.72 us | 219.87 us | 139.29 us |
| future-pay-out-2 | 814.15 us | 381.91 us | **335.25 us** | 230.67 us | 1.65 ms | 1.20 ms | 8.79 ms | 7.24 ms | 1.26 ms | 540.96 us | 443.64 us | 417.08 us | 320.83 us | 112.72 us | 1.42 ms | 1.20 ms | 702.73 us | 571.64 us | 783.66 us | 642.23 us | 592.23 us | 514.06 us | 608.46 us | 435.25 us | 156.84 us | 415.63 us | 300.82 us |
| future-pay-out-3 | 817.61 us | 380.26 us | **324.58 us** | 238.58 us | 1.65 ms | 1.20 ms | 8.59 ms | 7.16 ms | 1.27 ms | 539.69 us | 440.78 us | 419.02 us | 315.61 us | 113.73 us | 1.41 ms | 1.21 ms | 696.05 us | 564.32 us | 764.99 us | 631.61 us | 584.38 us | 503.09 us | 611.45 us | 441.68 us | 157.25 us | 419.79 us | 300.13 us |
| future-pay-out-4 | 1.45 ms | 581.23 us | **572.83 us** | 380.73 us | 3.88 ms | 3.04 ms | 16.02 ms | 13.12 ms | 2.14 ms | 957.64 us | 774.71 us | 698.35 us | 507.79 us | 302.75 us | 3.84 ms | 3.35 ms | 1.28 ms | 997.02 us | 1.33 ms | 1.09 ms | 1.04 ms | 896.02 us | 1.25 ms | 930.59 us | 281.81 us | 688.74 us | 476.23 us |
| future-settle-early-1 | 487.00 us | 180.22 us | **172.51 us** | 108.74 us | 881.80 us | 576.42 us | 4.49 ms | 3.22 ms | 622.21 us | 287.40 us | 214.43 us | 242.70 us | 170.63 us | 54.80 us | 732.64 us | 592.86 us | 369.47 us | 280.88 us | 398.94 us | 310.55 us | 305.06 us | 245.58 us | 341.90 us | 215.70 us | 66.27 us | 221.28 us | 139.12 us |
| future-settle-early-2 | 809.06 us | 374.23 us | **335.90 us** | 227.18 us | 1.63 ms | 1.18 ms | 8.68 ms | 7.12 ms | 1.27 ms | 540.35 us | 440.78 us | 433.24 us | 322.68 us | 111.31 us | 1.45 ms | 1.24 ms | 716.21 us | 573.56 us | 788.91 us | 646.81 us | 584.52 us | 511.60 us | 616.23 us | 442.38 us | 157.26 us | 416.12 us | 300.79 us |
| future-settle-early-3 | 809.88 us | 379.30 us | **326.97 us** | 234.72 us | 1.65 ms | 1.20 ms | 8.64 ms | 7.12 ms | 1.28 ms | 540.13 us | 441.66 us | 421.71 us | 314.75 us | 114.00 us | 1.46 ms | 1.25 ms | 711.26 us | 565.66 us | 784.23 us | 649.06 us | 592.51 us | 502.22 us | 618.04 us | 435.16 us | 155.32 us | 418.89 us | 301.04 us |
| future-settle-early-4 | 1.27 ms | 432.18 us | **495.64 us** | 300.33 us | 3.47 ms | 2.67 ms | 11.94 ms | 8.81 ms | 1.63 ms | 746.02 us | 567.41 us | 578.84 us | 384.22 us | 254.93 us | 3.23 ms | 2.81 ms | 974.23 us | 730.44 us | 1.04 ms | 794.25 us | 822.51 us | 697.44 us | 1.01 ms | 662.59 us | 225.53 us | 575.90 us | 368.26 us |
| game-sm-success_1-1 | 904.31 us | 272.28 us | **303.28 us** | 168.01 us | 1.47 ms | 851.43 us | 7.57 ms | 5.14 ms | 928.50 us | 476.15 us | 336.79 us | 432.65 us | 292.15 us | 101.06 us | 1.27 ms | 945.37 us | 591.45 us | 402.43 us | 648.24 us | 456.57 us | 523.64 us | 403.33 us | 616.72 us | 347.72 us | 111.74 us | 394.67 us | 216.77 us |
| game-sm-success_1-2 | 377.61 us | 146.89 us | **130.34 us** | 81.60 us | 687.01 us | 464.93 us | 3.31 ms | 2.26 ms | 396.34 us | 213.76 us | 162.78 us | 178.85 us | 128.75 us | 30.45 us | 607.51 us | 503.25 us | 258.27 us | 189.74 us | 273.86 us | 216.82 us | 244.05 us | 202.00 us | 266.36 us | 173.14 us | 51.12 us | 176.96 us | 115.51 us |
| game-sm-success_1-3 | 1.13 ms | 436.79 us | **420.05 us** | 262.61 us | 2.06 ms | 1.40 ms | 11.43 ms | 8.99 ms | 1.60 ms | 703.04 us | 561.64 us | 567.11 us | 406.68 us | 177.81 us | 1.89 ms | 1.54 ms | 912.56 us | 703.33 us | 1.02 ms | 800.17 us | 756.64 us | 652.21 us | 815.11 us | 553.13 us | 195.58 us | 520.24 us | 356.33 us |
| game-sm-success_1-4 | 398.49 us | 169.69 us | **148.68 us** | 97.21 us | 760.57 us | 535.51 us | 3.51 ms | 2.59 ms | 479.93 us | 237.67 us | 185.96 us | 195.55 us | 138.79 us | 34.96 us | 687.28 us | 587.05 us | 290.81 us | 219.56 us | 319.31 us | 250.19 us | 283.35 us | 229.68 us | 291.67 us | 200.16 us | 57.87 us | 191.72 us | 132.95 us |
| game-sm-success_2-1 | 903.70 us | 274.52 us | **295.91 us** | 160.94 us | 1.47 ms | 843.66 us | 7.63 ms | 5.08 ms | 950.44 us | 481.66 us | 341.19 us | 424.31 us | 292.08 us | 103.73 us | 1.28 ms | 949.43 us | 609.39 us | 407.34 us | 664.56 us | 458.88 us | 525.87 us | 398.63 us | 612.00 us | 348.51 us | 112.98 us | 392.73 us | 215.53 us |
| game-sm-success_2-2 | 371.91 us | 146.12 us | **129.31 us** | 82.39 us | 701.95 us | 464.06 us | 3.10 ms | 2.29 ms | 403.53 us | 212.13 us | 159.27 us | 178.64 us | 126.92 us | 31.01 us | 600.74 us | 509.74 us | 256.85 us | 193.12 us | 273.75 us | 211.75 us | 241.32 us | 202.97 us | 272.68 us | 173.45 us | 51.81 us | 173.18 us | 113.28 us |
| game-sm-success_2-3 | 1.13 ms | 446.87 us | **445.21 us** | 272.38 us | 2.06 ms | 1.40 ms | 11.65 ms | 8.81 ms | 1.55 ms | 702.94 us | 556.99 us | 552.53 us | 415.03 us | 176.43 us | 1.84 ms | 1.49 ms | 905.97 us | 710.27 us | 992.99 us | 788.06 us | 751.94 us | 637.12 us | 821.41 us | 551.13 us | 192.90 us | 536.35 us | 358.00 us |
| game-sm-success_2-4 | 404.27 us | 168.18 us | **145.74 us** | 97.09 us | 778.03 us | 521.50 us | 3.54 ms | 2.60 ms | 449.05 us | 239.61 us | 187.77 us | 194.39 us | 139.24 us | 34.91 us | 705.61 us | 602.82 us | 281.18 us | 221.13 us | 305.30 us | 239.92 us | 281.76 us | 230.84 us | 292.50 us | 200.08 us | 58.26 us | 192.04 us | 134.01 us |
| game-sm-success_2-5 | 1.12 ms | 435.35 us | **433.76 us** | 284.37 us | 2.08 ms | 1.40 ms | 11.58 ms | 8.99 ms | 1.54 ms | 704.32 us | 559.08 us | 565.95 us | 412.34 us | 170.58 us | 1.92 ms | 1.57 ms | 920.35 us | 726.19 us | 1.00 ms | 798.47 us | 762.37 us | 640.12 us | 830.07 us | 586.24 us | 194.22 us | 521.44 us | 355.98 us |
| game-sm-success_2-6 | 400.08 us | 170.03 us | **146.97 us** | 96.32 us | 779.16 us | 541.45 us | 3.46 ms | 2.68 ms | 445.90 us | 238.78 us | 187.06 us | 195.38 us | 140.74 us | 35.17 us | 695.69 us | 594.07 us | 286.02 us | 217.87 us | 319.20 us | 248.04 us | 257.54 us | 232.03 us | 308.04 us | 203.51 us | 59.71 us | 193.69 us | 134.50 us |
| guardrail-sorted-large | 579.22 us | 318.39 us | **294.29 us** | 225.25 us | 1.80 ms | 1.47 ms | 15.92 ms | 15.15 ms | 922.50 us | 392.99 us | 312.59 us | 1.16 ms | 786.28 us | 195.06 us | 1.50 ms | 1.21 ms | 533.57 us | 430.24 us | 590.48 us | 496.70 us | 742.89 us | 440.04 us | 421.95 us | 324.13 us | 239.89 us | 405.29 us | 275.58 us |
| guardrail-sorted-small | 180.55 us | 51.25 us | **72.28 us** | 42.88 us | 436.84 us | 320.31 us | 2.92 ms | 2.44 ms | 161.25 us | 89.99 us | 50.77 us | 253.28 us | 196.73 us | 72.41 us | 281.90 us | 212.94 us | 121.34 us | 66.24 us | 126.42 us | 74.98 us | 110.42 us | 83.55 us | 119.99 us | 56.37 us | 17.75 us | 93.34 us | 44.66 us |
| guardrail-unsorted-large | 719.07 us | 452.37 us | **381.57 us** | 337.65 us | 2.40 ms | 2.04 ms | 188.64 ms | 195.13 ms | 1.35 ms | 511.48 us | 430.90 us | 1.31 ms | 890.94 us | 245.75 us | 1.98 ms | 1.67 ms | 714.74 us | 621.30 us | 780.03 us | 695.50 us | 856.86 us | 588.87 us | 552.25 us | 453.26 us | 305.58 us | 501.06 us | 373.12 us |
| guardrail-unsorted-small | 181.11 us | 50.44 us | **69.71 us** | 42.04 us | 417.01 us | 312.08 us | 3.97 ms | 3.46 ms | 150.99 us | 88.11 us | 50.38 us | 251.10 us | 204.41 us | 70.37 us | 277.73 us | 210.23 us | 115.28 us | 64.71 us | 123.57 us | 73.13 us | 112.00 us | 84.00 us | 118.33 us | 55.38 us | 17.03 us | 94.25 us | 43.68 us |
| multisig-sm-01 | 984.83 us | 278.80 us | **317.07 us** | 166.21 us | 1.56 ms | 864.57 us | 8.53 ms | 5.83 ms | 983.07 us | 516.55 us | 362.87 us | 467.89 us | 320.54 us | 110.63 us | 1.30 ms | 989.71 us | 645.85 us | 438.40 us | 700.20 us | 488.45 us | 558.90 us | 437.72 us | 659.58 us | 366.19 us | 119.03 us | 401.67 us | 222.44 us |
| multisig-sm-02 | 952.27 us | 270.38 us | **311.09 us** | 164.84 us | 1.54 ms | 838.55 us | 8.43 ms | 5.65 ms | 980.14 us | 505.41 us | 352.03 us | 472.13 us | 305.72 us | 116.35 us | 1.32 ms | 968.57 us | 619.35 us | 423.36 us | 680.72 us | 461.99 us | 549.73 us | 429.00 us | 651.97 us | 359.65 us | 117.61 us | 401.94 us | 216.99 us |
| multisig-sm-03 | 970.25 us | 281.81 us | **301.58 us** | 157.09 us | 1.53 ms | 874.15 us | 8.54 ms | 5.59 ms | 963.15 us | 507.18 us | 355.66 us | 464.19 us | 319.35 us | 114.91 us | 1.31 ms | 933.55 us | 638.24 us | 427.81 us | 691.26 us | 481.65 us | 545.40 us | 426.16 us | 647.35 us | 360.44 us | 117.15 us | 402.67 us | 217.52 us |
| multisig-sm-04 | 969.75 us | 274.99 us | **300.77 us** | 165.41 us | 1.58 ms | 856.79 us | 8.40 ms | 5.58 ms | 962.98 us | 512.24 us | 361.02 us | 466.35 us | 301.89 us | 113.88 us | 1.32 ms | 1.01 ms | 647.11 us | 424.43 us | 705.75 us | 486.88 us | 561.19 us | 427.65 us | 657.46 us | 365.17 us | 121.30 us | 404.24 us | 222.05 us |
| multisig-sm-05 | 1.11 ms | 377.75 us | **397.98 us** | 229.97 us | 1.94 ms | 1.22 ms | 11.49 ms | 8.61 ms | 1.40 ms | 675.37 us | 517.91 us | 529.00 us | 372.87 us | 165.06 us | 1.76 ms | 1.39 ms | 857.11 us | 640.96 us | 908.61 us | 698.71 us | 734.61 us | 598.25 us | 796.51 us | 508.32 us | 170.90 us | 497.45 us | 315.76 us |
| multisig-sm-06 | 988.08 us | 272.79 us | **314.66 us** | 163.59 us | 1.57 ms | 867.01 us | 8.42 ms | 5.72 ms | 1.02 ms | 513.44 us | 362.36 us | 462.38 us | 312.94 us | 113.44 us | 1.29 ms | 984.99 us | 652.64 us | 429.37 us | 683.96 us | 482.37 us | 564.78 us | 434.58 us | 658.57 us | 365.54 us | 117.54 us | 403.46 us | 222.82 us |
| multisig-sm-07 | 956.29 us | 268.32 us | **300.40 us** | 159.19 us | 1.54 ms | 831.82 us | 8.27 ms | 5.60 ms | 1.02 ms | 504.82 us | 354.34 us | 466.11 us | 309.94 us | 113.43 us | 1.31 ms | 963.07 us | 621.50 us | 415.01 us | 678.46 us | 466.03 us | 548.96 us | 418.91 us | 655.68 us | 360.16 us | 115.45 us | 399.38 us | 236.43 us |
| multisig-sm-08 | 950.38 us | 269.11 us | **324.88 us** | 164.29 us | 1.52 ms | 839.62 us | 8.50 ms | 5.60 ms | 947.70 us | 511.10 us | 355.94 us | 461.03 us | 314.59 us | 113.85 us | 1.36 ms | 978.36 us | 627.72 us | 426.50 us | 691.11 us | 474.98 us | 551.99 us | 426.47 us | 647.27 us | 363.04 us | 121.30 us | 400.95 us | 219.56 us |
| multisig-sm-09 | 950.79 us | 275.38 us | **315.64 us** | 159.86 us | 1.57 ms | 875.34 us | 8.48 ms | 5.65 ms | 966.12 us | 514.65 us | 358.85 us | 462.28 us | 316.50 us | 118.73 us | 1.31 ms | 988.64 us | 642.23 us | 445.26 us | 691.57 us | 475.70 us | 558.70 us | 431.52 us | 656.57 us | 364.79 us | 111.66 us | 406.60 us | 222.85 us |
| multisig-sm-10 | 1.10 ms | 375.56 us | **398.82 us** | 248.58 us | 1.92 ms | 1.21 ms | 11.59 ms | 8.83 ms | 1.39 ms | 675.71 us | 514.02 us | 534.62 us | 385.79 us | 164.76 us | 1.78 ms | 1.40 ms | 846.32 us | 639.50 us | 926.73 us | 711.90 us | 719.03 us | 595.95 us | 799.06 us | 508.51 us | 171.53 us | 499.31 us | 311.94 us |
| ping-pong-1 | 831.39 us | 237.03 us | **259.69 us** | 140.38 us | 1.34 ms | 717.14 us | 7.36 ms | 4.89 ms | 801.85 us | 420.64 us | 290.67 us | 374.26 us | 244.17 us | 81.30 us | 1.09 ms | 800.05 us | 519.68 us | 358.93 us | 567.23 us | 388.24 us | 454.08 us | 344.57 us | 544.51 us | 298.12 us | 93.15 us | 338.80 us | 182.61 us |
| ping-pong-2 | 830.38 us | 228.60 us | **265.57 us** | 138.57 us | 1.32 ms | 704.52 us | 7.37 ms | 4.91 ms | 800.71 us | 420.85 us | 286.29 us | 385.83 us | 252.04 us | 81.84 us | 1.09 ms | 804.80 us | 533.65 us | 352.97 us | 566.11 us | 399.27 us | 452.46 us | 346.75 us | 544.78 us | 298.74 us | 95.71 us | 340.95 us | 183.86 us |
| ping-pong_2-1 | 712.96 us | 145.34 us | **203.25 us** | 83.32 us | 1.02 ms | 441.75 us | 5.22 ms | 2.80 ms | 470.68 us | 307.33 us | 173.42 us | 302.68 us | 177.06 us | 42.36 us | 787.04 us | 505.83 us | 384.54 us | 211.96 us | 408.93 us | 224.62 us | 322.44 us | 221.33 us | 418.46 us | 175.17 us | 55.47 us | 269.07 us | 112.83 us |
| prism-1 | 329.29 us | 118.63 us | **111.26 us** | 68.75 us | 625.86 us | 382.40 us | 2.74 ms | 1.81 ms | 347.25 us | 180.64 us | 133.51 us | 158.48 us | 110.66 us | 24.50 us | 515.80 us | 428.72 us | 219.59 us | 158.89 us | 232.93 us | 175.23 us | 201.55 us | 164.14 us | 233.82 us | 145.55 us | 40.67 us | 150.93 us | 95.51 us |
| prism-2 | 904.90 us | 284.23 us | **320.00 us** | 175.58 us | 1.55 ms | 900.88 us | 8.56 ms | 6.17 ms | 978.60 us | 498.46 us | 357.26 us | 441.51 us | 301.88 us | 102.24 us | 1.32 ms | 995.27 us | 622.06 us | 439.32 us | 674.61 us | 487.51 us | 553.93 us | 432.15 us | 636.99 us | 375.91 us | 116.04 us | 398.71 us | 230.27 us |
| prism-3 | 574.76 us | 258.08 us | **234.00 us** | 161.38 us | 1.16 ms | 830.84 us | 6.27 ms | 5.06 ms | 879.55 us | 404.61 us | 327.68 us | 296.63 us | 227.56 us | 74.71 us | 1.05 ms | 906.82 us | 499.61 us | 404.31 us | 522.56 us | 433.17 us | 419.42 us | 367.75 us | 455.02 us | 331.19 us | 102.07 us | 299.55 us | 211.90 us |
| pubkey-1 | 312.31 us | 100.46 us | **100.63 us** | 57.42 us | 559.41 us | 327.08 us | 2.40 ms | 1.45 ms | 300.13 us | 160.81 us | 111.70 us | 143.95 us | 99.27 us | 20.11 us | 452.02 us | 366.96 us | 192.38 us | 130.51 us | 206.32 us | 146.00 us | 174.48 us | 135.25 us | 209.13 us | 119.82 us | 36.31 us | 135.32 us | 81.38 us |
| stablecoin_1-1 | 1.54 ms | 665.09 us | **756.42 us** | 466.53 us | 5.69 ms | 4.64 ms | 17.91 ms | 14.00 ms | 2.29 ms | 1.14 ms | 929.66 us | 943.73 us | 724.83 us | 598.56 us | 6.03 ms | 5.36 ms | 1.51 ms | 1.18 ms | 1.55 ms | 1.23 ms | 1.34 ms | 1.18 ms | 1.50 ms | 1.08 ms | 334.17 us | 834.60 us | 578.34 us |
| stablecoin_1-2 | 373.13 us | 141.67 us | **129.63 us** | 79.11 us | 686.17 us | 503.80 us | 3.16 ms | 2.21 ms | 377.97 us | 208.50 us | 157.40 us | 172.96 us | 125.11 us | 29.60 us | 588.09 us | 496.08 us | 251.97 us | 184.90 us | 271.75 us | 205.14 us | 249.70 us | 190.78 us | 263.06 us | 171.74 us | 50.35 us | 170.61 us | 112.72 us |
| stablecoin_1-3 | 1.87 ms | 765.80 us | **803.53 us** | 513.88 us | 6.04 ms | 5.19 ms | 20.87 ms | 17.04 ms | 2.63 ms | 1.36 ms | 1.11 ms | 1.08 ms | 860.96 us | 719.90 us | 6.58 ms | 5.96 ms | 1.68 ms | 1.36 ms | 1.76 ms | 1.44 ms | 1.56 ms | 1.35 ms | 1.68 ms | 1.26 ms | 365.90 us | 918.41 us | 658.72 us |
| stablecoin_1-4 | 375.89 us | 151.86 us | **135.63 us** | 83.97 us | 727.30 us | 486.82 us | 3.32 ms | 2.42 ms | 398.19 us | 223.26 us | 174.28 us | 179.48 us | 126.56 us | 30.70 us | 626.29 us | 529.66 us | 266.11 us | 197.73 us | 279.02 us | 216.26 us | 254.12 us | 201.39 us | 273.77 us | 180.06 us | 54.33 us | 179.44 us | 124.18 us |
| stablecoin_1-5 | 2.10 ms | 979.24 us | **963.10 us** | 679.17 us | 6.71 ms | 5.64 ms | 25.38 ms | 21.55 ms | 3.32 ms | 1.65 ms | 1.45 ms | 1.24 ms | 1.03 ms | 832.57 us | 7.70 ms | 6.94 ms | 2.10 ms | 1.75 ms | 2.20 ms | 1.84 ms | 1.96 ms | 1.77 ms | 2.05 ms | 1.62 ms | 422.97 us | 1.10 ms | 832.46 us |
| stablecoin_1-6 | 455.01 us | 200.86 us | **155.75 us** | 106.04 us | 853.29 us | 599.79 us | 3.82 ms | 2.86 ms | 497.66 us | 259.28 us | 205.49 us | 204.45 us | 150.66 us | 38.01 us | 755.13 us | 655.16 us | 313.01 us | 242.96 us | 330.55 us | 263.80 us | 317.64 us | 251.02 us | 312.49 us | 218.29 us | 64.71 us | 209.58 us | 148.75 us |
| stablecoin_2-1 | 1.56 ms | 671.27 us | **775.63 us** | 502.74 us | 5.70 ms | 4.66 ms | 18.03 ms | 14.17 ms | 2.30 ms | 1.14 ms | 934.54 us | 939.72 us | 730.16 us | 666.45 us | 5.99 ms | 5.38 ms | 1.51 ms | 1.17 ms | 1.57 ms | 1.24 ms | 1.33 ms | 1.16 ms | 1.50 ms | 1.08 ms | 333.15 us | 838.87 us | 574.81 us |
| stablecoin_2-2 | 371.29 us | 138.31 us | **127.19 us** | 81.88 us | 680.15 us | 449.64 us | 3.15 ms | 2.37 ms | 383.36 us | 212.44 us | 158.02 us | 172.30 us | 122.09 us | 29.49 us | 599.25 us | 509.34 us | 244.25 us | 186.00 us | 272.40 us | 207.67 us | 238.72 us | 199.57 us | 260.01 us | 168.41 us | 50.27 us | 172.56 us | 111.79 us |
| stablecoin_2-3 | 1.82 ms | 766.39 us | **805.30 us** | 526.88 us | 6.06 ms | 5.24 ms | 20.23 ms | 16.94 ms | 2.63 ms | 1.35 ms | 1.11 ms | 1.11 ms | 903.45 us | 731.04 us | 6.57 ms | 5.90 ms | 1.69 ms | 1.36 ms | 1.78 ms | 1.44 ms | 1.55 ms | 1.34 ms | 1.66 ms | 1.26 ms | 366.56 us | 917.23 us | 667.75 us |
| stablecoin_2-4 | 376.14 us | 152.00 us | **131.16 us** | 83.76 us | 734.45 us | 479.71 us | 3.27 ms | 2.42 ms | 402.31 us | 219.84 us | 167.85 us | 179.50 us | 128.88 us | 31.01 us | 622.71 us | 542.63 us | 263.25 us | 196.87 us | 278.50 us | 215.20 us | 251.94 us | 204.88 us | 272.04 us | 179.09 us | 52.10 us | 179.72 us | 120.82 us |
| token-account-1 | 433.18 us | 136.95 us | **144.12 us** | 79.80 us | 736.36 us | 446.24 us | 3.90 ms | 2.55 ms | 469.01 us | 236.83 us | 166.88 us | 199.88 us | 132.92 us | 40.13 us | 606.60 us | 485.72 us | 290.79 us | 206.62 us | 309.54 us | 223.49 us | 246.17 us | 191.37 us | 291.49 us | 166.21 us | 48.58 us | 186.80 us | 106.46 us |
| token-account-2 | 532.05 us | 235.19 us | 272.15 us | 146.66 us | 1.07 ms | 786.61 us | 4.67 ms | 3.42 ms | 780.59 us | 343.25 us | 279.27 us | **270.33 us** | 208.98 us | 66.15 us | 925.86 us | 809.16 us | 452.09 us | 361.35 us | 482.11 us | 391.18 us | 373.81 us | 292.50 us | 393.47 us | 275.03 us | 96.03 us | 266.21 us | 189.44 us |
| uniswap-1 | 580.08 us | 281.51 us | **248.84 us** | 187.64 us | 1.29 ms | 968.61 us | 6.13 ms | 4.90 ms | 1.07 ms | 414.43 us | 347.13 us | 321.11 us | 255.42 us | 96.28 us | 1.07 ms | 929.40 us | 564.73 us | 459.19 us | 604.43 us | 528.05 us | 431.52 us | 386.22 us | 461.71 us | 334.19 us | 124.21 us | 313.64 us | 228.31 us |
| uniswap-2 | 461.51 us | 158.07 us | **157.96 us** | 94.95 us | 821.35 us | 514.54 us | 4.31 ms | 3.06 ms | 519.04 us | 266.00 us | 195.02 us | 218.07 us | 153.02 us | 43.41 us | 691.04 us | 557.49 us | 327.76 us | 239.49 us | 350.48 us | 260.16 us | 284.65 us | 228.16 us | 327.35 us | 198.26 us | 60.71 us | 208.13 us | 129.67 us |
| uniswap-3 | 2.15 ms | 1.19 ms | **980.97 us** | 742.29 us | 5.04 ms | 4.18 ms | 22.60 ms | 21.44 ms | 3.95 ms | 1.69 ms | 1.48 ms | 1.52 ms | 1.26 ms | 440.13 us | 5.15 ms | 4.59 ms | 2.15 ms | 1.88 ms | 2.38 ms | 2.10 ms | 1.82 ms | 1.64 ms | 1.92 ms | 1.55 ms | 441.77 us | 1.19 ms | 968.54 us |
| uniswap-4 | 501.57 us | 238.64 us | **197.70 us** | 140.66 us | 1.06 ms | 756.71 us | 4.48 ms | 3.66 ms | 661.50 us | 329.60 us | 267.41 us | 262.75 us | 194.99 us | 47.75 us | 994.39 us | 867.93 us | 410.77 us | 331.88 us | 425.32 us | 355.13 us | 399.94 us | 318.62 us | 393.23 us | 287.93 us | 87.16 us | 264.07 us | 195.22 us |
| uniswap-5 | 1.71 ms | 804.14 us | **682.30 us** | 493.88 us | 3.61 ms | 2.64 ms | 16.13 ms | 13.20 ms | 2.50 ms | 1.13 ms | 939.81 us | 1.08 ms | 833.47 us | 270.74 us | 3.46 ms | 2.97 ms | 1.43 ms | 1.18 ms | 1.59 ms | 1.32 ms | 1.24 ms | 1.09 ms | 1.30 ms | 939.21 us | 299.07 us | 863.18 us | 629.40 us |
| uniswap-6 | 491.03 us | 236.22 us | **194.75 us** | 137.64 us | 1.03 ms | 730.19 us | 4.48 ms | 3.47 ms | 629.21 us | 321.12 us | 258.44 us | 252.95 us | 187.53 us | 48.89 us | 976.39 us | 849.31 us | 395.38 us | 318.99 us | 408.04 us | 341.55 us | 383.57 us | 302.96 us | 377.41 us | 274.51 us | 83.80 us | 251.96 us | 186.33 us |
| vesting-1 | 660.28 us | 247.68 us | **243.60 us** | 151.49 us | 1.20 ms | 785.95 us | 5.80 ms | 4.21 ms | 883.74 us | 388.62 us | 296.17 us | 322.20 us | 232.19 us | 80.17 us | 966.08 us | 791.38 us | 491.57 us | 378.40 us | 533.01 us | 408.98 us | 406.31 us | 330.73 us | 457.69 us | 286.33 us | 96.74 us | 305.71 us | 193.69 us |

## VMs in this benchmark

| VM | Language | Runtime | Execution model | Version | Source | Home | Used by | Badges | Note |
|---|---|---|---|---|---|---|---|---|---|
| Scalus CEK (Scala / JVM) | Scala | GraalVM | Interpreter (CEK) | [v1.4.1](https://github.com/scalus3/scalus/releases/tag/v1.4.1) | [scalus3/scalus](https://github.com/scalus3/scalus) | [scalus.org](https://scalus.org) | [Hydrozoa](https://github.com/cardano-hydrozoa/hydrozoa) (L2), [Bifrost](https://github.com/FluidTokens/ft-bifrost-bridge) (bridge), [Cardano Client Lib](https://github.com/bloxbean/cardano-client-lib) (SDK), [Yaci Store](https://github.com/bloxbean/yaci-store) (indexer), [Yaci DevKit](https://github.com/bloxbean/yaci-devkit) (dev tool) | - | - |
| Plutigo (Go) | Go | native | Interpreter (CEK) | [v0.10.0](https://github.com/blinklabs-io/plutigo/releases/tag/v0.10.0) | [blinklabs-io/plutigo](https://github.com/blinklabs-io/plutigo) | - | [Dingo](https://github.com/blinklabs-io/dingo) (node) | - | - |
| amaru-uplc (Rust) | Rust | native | Interpreter (AST walker) | [amaru-uplc 0.4.0](https://github.com/pragma-org/amaru/tree/ddd3fdfc1c01b29d09a4dd59f4ecd2872062153b/crates/amaru-uplc) | [pragma-org/amaru](https://github.com/pragma-org/amaru) | - | [Amaru](https://github.com/pragma-org/amaru) (node) | - | - |
| plutus-core (Haskell / GHC) | Haskell | GHC | Interpreter (CEK) | [1.70.0.0](https://github.com/IntersectMBO/plutus/releases/tag/1.70.0.0) | [IntersectMBO/plutus](https://github.com/IntersectMBO/plutus) | [plutus.cardano.intersectmbo.org](https://plutus.cardano.intersectmbo.org) | [cardano-node](https://github.com/IntersectMBO/cardano-node) (node) | - | - |
| Scalus.js CEK (Scala.js / Node V8) | Scala.js | Node (V8) | Interpreter (CEK) | [scalus 1.4.1 (npm)](https://github.com/scalus3/scalus/releases/tag/v1.4.1) | [scalus3/scalus](https://github.com/scalus3/scalus) | [scalus.org](https://scalus.org) | [Lucid Evolution](https://github.com/Anastasia-Labs/lucid-evolution) (SDK), [MeshJS](https://github.com/MeshJS/mesh) (SDK), [Evolution SDK](https://github.com/IntersectMBO/evolution-sdk) (SDK) | - | - |
| Aiken uplc (Rust) | Rust | native | Interpreter (CEK) | [v1.1.24](https://github.com/aiken-lang/aiken/releases/tag/v1.1.24) | [aiken-lang/aiken](https://github.com/aiken-lang/aiken) | [aiken-lang.org](https://aiken-lang.org) | [Aiken](https://aiken-lang.org) (compiler), [Blaze SDK](https://github.com/butaneprotocol/blaze-cardano) (SDK) | - | Aiken v1.1.24 copies the CEK environment on every lambda application (quadratic in recursion depth). aiken main fixes it (PRs [#1451](https://github.com/aiken-lang/aiken/pull/1451), [#1452](https://github.com/aiken-lang/aiken/pull/1452): coop-6 92 ms -> 1.2 ms), but no release contains the fix yet. |
| Aiken uplc WASM (Rust → WASM / Node V8) | Rust → WASM | Node (V8) | Interpreter (CEK) | [@lucid-evolution/uplc 0.4.0](https://github.com/Anastasia-Labs/lucid-evolution/releases/tag/@lucid-evolution/uplc@0.4.0) | [Anastasia-Labs/lucid-evolution](https://github.com/Anastasia-Labs/lucid-evolution) | [anastasia-labs.github.io/lucid-evolution](https://anastasia-labs.github.io/lucid-evolution/) | [Lucid Evolution](https://github.com/Anastasia-Labs/lucid-evolution) (SDK) | decode cached (by the library) | Built from [colll78/aiken](https://github.com/colll78/aiken) (aiken main plus fixes), which includes the CEK fixes that v1.1.24 lacks. |
| Scalus JIT (Scala / JVM) | Scala | GraalVM | JIT compiler (UPLC → JVM bytecode) | [v1.4.1](https://github.com/scalus3/scalus/releases/tag/v1.4.1) | [scalus3/scalus](https://github.com/scalus3/scalus) | [scalus.org](https://scalus.org) | - | experimental: no downstream user, decode and compile excluded | - |
| blaze-plutus (TypeScript / Node V8) | TypeScript | Node (V8) | Interpreter (CEK) | [@blaze-cardano/plutus 0.1.1](https://github.com/butaneprotocol/blaze-cardano/releases/tag/@blaze-cardano/plutus@0.1.1) | [butaneprotocol/blaze-cardano](https://github.com/butaneprotocol/blaze-cardano) | [blaze.butane.dev](https://blaze.butane.dev) | - | experimental: no downstream user | - |
| Chrysalis (C# / .NET JIT) | C# | .NET 10 (JIT) | Interpreter (CEK) | [Chrysalis.Plutus 1.7.14-alpha (NuGet)](https://www.nuget.org/packages/Chrysalis.Plutus/1.7.14-alpha) | [SAIB-Inc/Chrysalis](https://github.com/SAIB-Inc/Chrysalis) | - | - | experimental: pre-release only | - |
| Chrysalis AOT (C# / .NET AOT) | C# | .NET 10 (NativeAOT) | Interpreter (CEK) | [Chrysalis.Plutus 1.7.14-alpha (NuGet)](https://www.nuget.org/packages/Chrysalis.Plutus/1.7.14-alpha) | [SAIB-Inc/Chrysalis](https://github.com/SAIB-Inc/Chrysalis) | - | - | experimental: pre-release only | - |
| Julc Java CEK (Java / JVM) | Java | GraalVM | Interpreter (CEK) | [v0.1.0-pre19](https://github.com/bloxbean/julc/releases/tag/v0.1.0-pre19) | [bloxbean/julc](https://github.com/bloxbean/julc) | - | - | experimental: pre-release only | - |
| Plutuz (Zig) | Zig | native | Interpreter (CEK) | [main 33b812d](https://github.com/utxo-company/plutuz/commit/33b812d) | [utxo-company/plutuz](https://github.com/utxo-company/plutuz) | - | - | experimental: no release | - |
| llvm-uplc JIT (C++ / LLVM) | C / C++ | native (LLVM 22 LLJIT) | JIT compiler (UPLC → native code) | [main 6bcef67](https://github.com/SeungheonOh/llvm-uplc/commit/6bcef67) | [SeungheonOh/llvm-uplc](https://github.com/SeungheonOh/llvm-uplc) | - | - | outdated cost model, experimental: outdated, decode and compile excluded | - |
| amaru-uplc BC (fork) (Rust) | Rust | native | Bytecode VM (UPLC → bytecode) | [fork 069cef5](https://github.com/jonathanlim222/uplc/commit/069cef5) | [jonathanlim222/uplc](https://github.com/jonathanlim222/uplc) | - | - | experimental: no release | - |

---
Harness commit: [`92dd521e2`](https://github.com/lantr-io/plutus-vm-benchmark/commit/92dd521e27c490ce308a22ce2acd294f5bae7308)

*Plutus VM Benchmark – maintained by [Lantr](https://lantr.io) – Alexander Nemish. Forked from [SAIB-Inc/cardano-plutus-vm-benchmark](https://github.com/SAIB-Inc/cardano-plutus-vm-benchmark) by SAIB Inc. and contributors. MIT License, original work © 2025 SAIB Inc., © 2026 Lantr. Source: [lantr-io/plutus-vm-benchmark](https://github.com/lantr-io/plutus-vm-benchmark)*