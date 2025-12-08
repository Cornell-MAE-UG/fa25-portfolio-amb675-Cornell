---
layout: project
title: Torque Wrench Design
description: Mechanics of Materials Final Project
technologies: [Matlab, Fusion360, Ansys]
image: /assets\images\mechofmatsMATLABconfiguration.jpg
---

As the final project of mechanics of materials, we were asked to design a torque wrench. Our wrench was to sustain a torque of T = ±600 in-lbf for 10^6 cycles and 
- attain at least 1.0 mV/V output
- attain a safety factor of Xo = 4 for yield or brittle failure
- safety factor of XK = 2 for crack growth from an assumed crack of depth 0.04 inches
(1 mm)
- fatigue stress safety factor of XS = 1.5
- be made of a steel, aluminum or titanium alloy

The hand calculations for our design were done in a matlab script.  
```matlab
    a = 0.04; % crack length
    M = 600; % max torque 
    c = 1.0; % distance from center of drive to center of strain gauge

    % material properties
    E = 17.E6; % Young's modulus psi
    nu = 0.37; % Poisson's ratio
    su = 132.E3; % tensile strength use yield or ultimate depending on material psi
    KIC = 97.E3; % fracture toughness psi sqrtin
    sfatigue = 69.e3; % fatigue strength from Granta for 10^6 cycles 
    name = 'Ti-6Al-4V' % Ti-6Al-4V alpha beta annealed 

    %dimensional properties
    L = 16; % length from drive to where load applied (inches)
    h = .6; % width
    b = .4; % thickness

    %Stress and deflection analysis
    I = (b * h^3) / 12;
    sigma =  M*(h/2)/I; % Max normal stress
    sigma_norm_ksi = sigma / 1000 % Convert to ksi
    load_point_deflection = (M * L^2) / (3 * E * I)
    F = M/L;
    Mgage = F*(L-c);
    sigma_g=  Mgage*(h/2)/I; 
    k = 2;
    epsilon1 = sigma_g / E;
    epsilon2 = -epsilon1;
    vout_vin = k/4 * 2*epsilon1; % THIS IS CORRECT
    strain = epsilon1/10^-3
    voltageOutput = vout_vin/10^-3

    Ki= 1.12*sigma*sqrt(pi*a);
    X_y_strength = su / sigma
    X_CrackGrowth = KIC/Ki
    X_Fatigue = sfatigue / abs(sigma) % Safety factor for fatigue
```
We chose to use titanium, 'Ti-6Al-4V', as in this theoretical design price was not an issue and titanium is both light and strong. This design gave us factors of safety of:
X_yield_strength = 5.2800
X_CrackGrowth = 9.7726
X_Fatigue = 2.7600
and a voltage output of 1.3787mV/V

Our dimensions were decided by iterating thorugh our hand calculation script until we found a set of dimensions that met all criteria. 

Below is our ANSYS of the initial base case design and our final design.  

![Photo of old radio]({{ "/assets/images/old-radio.jpg" | relative_url }}){: .inline-image-l}
