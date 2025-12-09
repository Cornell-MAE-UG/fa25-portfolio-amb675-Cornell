---
layout: project
title: Torque Wrench Design
description: Mechanics of Materials Final Project
technologies: [Matlab, Fusion360, Ansys]
image: /assets/images/mech of mats/Screenshot 2025-12-08 at 20-49-46 materials reqs & hw - Google Docs.png
---
As the final project of mechanics of materials, we were asked to design a torque wrench. 

Our wrench was to sustain a torque of T = ±600 in-lbf for 10^6 cycles and 
- attain at least 1.0 mV/V output
- attain a safety factor of Xo = 4 for yield or brittle failure
- safety factor of XK = 2 for crack growth from an assumed crack of depth 0.04 inches
(1 mm)
- fatigue stress safety factor of XS = 1.5
- be made of a steel, aluminum or titanium alloy

---
##### Hand Calculations
The hand calculations for our design were done in a MATLAB script.  
```matlab
    %TIME TO DESIGN MY OWN
    %1mV/V output at 600 inlbf
    %X_Yield_strength = 4 
    %X_CrackGrowth = 2 is a = 0.04
    %X_fatigue = 1.5
    %steel, al, or titanium

    a = 0.04; % crack length
    M = 600; % max torque
    c = 1.0; % distance from center of drive to center of strain gauge

    % material properties
    E = 17.E6; % Young's modulus psi
    nu = 0.37; % Poisson's ratio
    su = 132.E3; % tensile strength use yield or ultimate depending on material psi
    KIC = 97.E3; % fracture toughness psi sqrtin
    sfatigue = 69.e3; % fatigue strength from Granta for 10^6 cycles
    name = 'Ti-6Al-4V' % Ti-6Al-4V aalpha beta annealed

    %dimensional properties
    L = 16; % length from drive to where load applied (inches)
    h = .6; % width
    b = .4; % thickness

    %Stress and deflection analysis
    I = (b * h^3) / 12;
    sigma =  M*(h/2)/I;
    sigma_norm_ksi = sigma / 1000 % Convert to ksi
    load_point_deflection = (M * L^2) / (3 * E * I)
    F = M/L;
    Mgage = F*(L-c);
    sigma_g=  Mgage*(h/2)/I;
    k = 2;
    epsilon1 = sigma_g / E;
    epsilon2 = -epsilon1;
    vout_vin = k/4 * 2*epsilon1; % THIS IS CORRECT formula value
    strain = epsilon1/10^-3
    voltageOutput = vout_vin/10^-3

    Ki= 1.12*sigma*sqrt(pi*a);
    X_y_strength = su / sigma
    X_CrackGrowth = KIC/Ki
    X_Fatigue = sfatigue / abs(sigma) % Safety factor for fatigue
```
---
##### Material Choice
We chose to use titanium, 'Ti-6Al-4V', as in this theoretical design price was not an issue and titanium is both light and strong. Below are listed the material properities:
Material properties:
- E = 17×10⁶ psi
- ν = 0.37
- σᵧ = 132×10³ psi
- K_IC = 97×10³ psi√in
- S_fatigue = 69×10³ psi

##### Calculated Values
This produced:
- Yield safety factor: 5.28
- Crack-growth safety factor: 9.77
- Fatigue safety factor: 2.76
- Output: 1.3787 mV/V
Our dimensions were decided by iterating thorugh our hand calculation script until we found a set of dimensions that met all criteria. 

---

##### My CAD:
<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/mech of mats/Screenshot 2025-12-08 at 20-49-46 materials reqs & hw - Google Docs.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
</div> 

---

##### Strain Gauge Selected: 
SGT-1LH/350-TY11 1.8 mm Grid Length, 5 mm Grid Width 350 Ω Resistance ST STC Number

Link: https://www.dwyeromega.com/en-us/uniaxial-half-bridge-strain-gauges-with-transducer-quality/SGT-Half-Bridge-Uniaxial/p/SGT-1LH-350-TY11 

It is sensitive enough that our strain max is 30,000 µm and has a carrier length 9.2 mm and a carrier width 4 mm, this fits in our spot as that is 0 36 in x 0.16 in.

---

##### FEM Results  
- Load Point Deflection: .503 in
- Strain @ gauge location: 1.4533e-003 in/in
- Max Normal Stress: 45.38 ksi

<div style="display:flex; flex-direction:column; gap:20px;">

<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/mech of mats/Screenshot 2025-12-08 at 20-50-07 materials reqs & hw - Google Docs.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />

<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/mech of mats/Screenshot 2025-12-08 at 20-50-17 materials reqs & hw - Google Docs.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/mech of mats/Screenshot 2025-12-08 at 20-50-37 materials reqs & hw - Google Docs.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />

<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/mech of mats/Screenshot 2025-12-08 at 20-50-47 materials reqs & hw - Google Docs.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />

<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/mech of mats/Screenshot 2025-12-08 at 20-51-01 materials reqs & hw - Google Docs.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
</div>

