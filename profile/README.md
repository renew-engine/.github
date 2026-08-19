<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/renew-banner-wide.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/renew-banner-wide-light.svg">
  <img src="assets/renew-banner-wide.svg" alt="renew, an AI-first game engine in Rust" width="820">
</picture>

<br>
<br>

### A game engine in Rust, built to be *operated*

<br>

</div>

Most engines are built around an editor, and everything else reaches the engine through whatever
that editor exposes. renew is built the other way around. Every capability is a library with a
command-line face and machine-readable output, so a developer at a terminal, a build script, a CI
job and an autonomous agent all drive it the same way. That is what *AI-first* means here.

The simulation underneath is bit-deterministic: same build, same seed, same inputs, same result,
byte for byte. CI checks that on five targets at once, desktop and mobile, and a digest that
differs anywhere fails the build.

<table>
<tr>
<td width="33%"><img src="assets/shot-arena.png" alt="A voxel arena seen from above, its walls and floor lit"></td>
<td width="33%"><img src="assets/shot-digging.png" alt="First-person view of a voxel floor with a block broken out of it and debris particles"></td>
<td width="33%"><img src="assets/shot-glide.png" alt="A side-scrolling game frame: a yellow bird between green pipes on a blue sky"></td>
</tr>
</table>

<sub>Left and centre: <code>cube</code>. Right: <code>glide</code>. Two of the six samples that ship with the engine, and each picture was produced by the sample it shows.</sub>

<div align="center">

<br>

## **[github.com/renew-engine/renew](https://github.com/renew-engine/renew)**

Apache-2.0&nbsp; · &nbsp;Published at 0.1.1&nbsp; · &nbsp;Early development

[![CI](https://github.com/renew-engine/renew/actions/workflows/ci.yml/badge.svg)](https://github.com/renew-engine/renew/actions/workflows/ci.yml) [![Nightly checks](https://github.com/renew-engine/renew/actions/workflows/nightly-checks.yml/badge.svg)](https://github.com/renew-engine/renew/actions/workflows/nightly-checks.yml)

</div>
