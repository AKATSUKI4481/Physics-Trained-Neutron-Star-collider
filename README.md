# Kilonova (Real-Time Relativistic Visualization Engine)

Single-file `index.html` browser simulation of a binary neutron star merger and kilonova, built with Three.js + custom GLSL ray-marched volumetrics.

No build system. No assets. Physics-informed real-time rendering.

---

## Overview

This project simulates the qualitative evolution of a binary neutron star (BNS) system:

1. Inspiral (PN-inspired regime)  
2. Merger / Prompt Collision  
3. Post-merger Kilonova Expansion  
4. Jet / GRB / Cocoon phenomenology  

The model is physics-motivated but computationally compressed to run in real time on consumer GPUs.

This is not GRMHD + Monte Carlo radiative transfer.  
It is a structured surrogate model designed for visual and conceptual accuracy.

---

## Physical Modeling (Approximation Layer)

### Inspiral Phase (Act I)

- Post-Newtonian-inspired phase acceleration  
- Chirp-mass and symmetric mass ratio scaling  
- Love-number–style tidal deformability proxy  
- Bar-mode onset near contact  
- Shear heating and Doppler beaming terms  
- L1 mass-transfer bridge with KH-like rolls  

Orbital phase evolution follows a PN-inspired scaling, not a simple Keplerian orbit.

---

### Merger Phase (Act II)

- Prompt flash luminosity proxy  
- Transient remnant emission  
- Shock-driven burst particle ejecta  
- Relativistic-style forward-beaming emphasis  
- Short-timescale detector-overwhelm effect  

The merger is temporally compressed but respects the relative energy hierarchy.

---

### Kilonova Expansion (Act III)

Multi-component ejecta geometry:

- Polar component  
  Fast, lanthanide-poor, bluer emission.

- Equatorial tidal ejecta  
  Slower, lanthanide-rich, redder emission.

- Jet / cocoon channel  
  Axis-aligned anisotropic emissivity with shock-ring evolution.

Dynamical scaling:

- Homologous expansion (v ~ r/t)  
- Diffusion-time-based luminosity evolution  
- Free-expansion → Sedov-like blending surrogate  

---

## Radiation & Thermodynamics Surrogates

- r-process heating proxy: Q ∝ t^-1.3  
- Thermalization efficiency evolution  
- Diffusion-time scaling per component  
- Photosphere recession proxy  
- Temperature evolution from luminosity and radius scaling  
- Optical depth (tau) modulation per component  
- Opacity contrast tied to lanthanide fraction surrogate  

---

## Spectral & Color Modeling

Instead of simple RGB tinting:

- 7-band pseudo-spectral transport (UV → NIR)  
- Planck-band sampling  
- Optical-depth–dependent blanketing  
- Recombination-dependent color evolution  
- Multi-band → CIE XYZ → linear sRGB mapping  
- Time-evolving blue → purple → red balance  

This produces physically plausible chromatic evolution without full radiative transfer.

---

## Transport & Viewing Effects

- Light-travel-time retardation approximation  
- Henyey–Greenstein-like anisotropic scattering surrogate  
- Relativistic-style Doppler beaming terms  
- Axis-dependent jet visibility weighting  
- Shock-ring angular projection logic  

Observer orientation materially changes the event.

---

## Instability Surrogates

- Rayleigh–Taylor-like interface fingering  
- Kelvin–Helmholtz-like shear rolls  
- Procedural turbulence (multi-octave FBM)  
- Domain-warped volumetric density  

These are structured noise fields, constrained to resemble physical instabilities.

---

## Rendering Architecture

- Full-screen volumetric ray marching  
- Multi-resolution volume buffer  
- Temporal accumulation / history blending  
- Adaptive quality tiers (Ultra → Low)  
- Multi-pass composite pipeline:
  - Bloom  
  - Chromatic aberration  
  - Sharpen  
  - Exposure smoothing  
- Screen-space GRB flash model  
- Shock-ring compositing  

The renderer balances stability and physical plausibility.

---

## Performance Design

- Browser-native (no bundlers)  
- Single HTML file  
- Three.js from CDN  
- Automatic quality adaptation  
- Camera-motion–aware temporal reset  
- Resolution-scaled volume buffers  

Designed to run smoothly on laptop GPUs.

---

## Controls

Real-time adjustable parameters:

- Neutron star masses  
- Separation scale  
- Ejecta mass  
- Polar / equatorial velocities  
- Opacity contrast  
- RT instability strength  
- Jet angle & intensity  
- Remnant luminosity  
- Bloom / chromatic aberration / sharpening  
- Manual or auto quality tier  

Free camera:
- Orbit  
- Pan  
- Zoom  

---

## Scientific Positioning

This is a real-time, physics-informed visualization engine.

It is appropriate for:
- Conceptual exploration  
- Educational visualization  
- Presentation rendering  
- Parameter sensitivity intuition  

It is not:
- A GRMHD solver  
- A radiation transport code  
- A quantitatively predictive astrophysical tool  

---

## Why This Exists

Full neutron star merger simulations require:

- GRMHD solvers  
- Nuclear reaction networks  
- Monte Carlo radiative transfer  
- HPC clusters  

This project compresses those qualitative behaviors into a coherent real-time surrogate.

It sits at the boundary between visualization, astrophysical intuition, and computational artistry.
