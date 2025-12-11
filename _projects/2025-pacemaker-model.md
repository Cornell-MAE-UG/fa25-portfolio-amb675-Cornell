---
layout: project
title: Modeling of a Pacemaker
description: Final Project for System Dynamics
technologies: [Matlab]
image: '/assets/images/systems/pacemaker+heart.png'
---
[Download our project write-up]({{ 'assets/Files/MAE3260_Final_Group_Work_Report.pdf' | relative_url }}) in PDF format.

Our final project for MAE 3260, System Dynamics, was to model a system of our choice so our group chose to model the heart and a pacemaker. 

My contribution was that I dound and read a Yahalom & Puzanov “Feedback stabilization applied to heart rhythm dynamics with integro-differential equations method.”, from which I produced an ODE to model the heartbeat. I then wrote a MATLAB script to model the heartbeat based on the paper and a pacemaker model more so based on intuition and general descriptions of the pacemaker. 

Below is are the images of our Van der Pol modeling of the heartbeat, our pacemaker signal model, and the heart beat with the signal. 


<div style="display:flex; flex-direction:column; gap:20px;">

<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/systems/heartbeat.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
    </div>
<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/systems/pacemaker.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
    </div>
<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/systems/pacemaker+heart.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
    </div>
</div>

---
##### Code
Below is my MATLAB code:

```matlab
    %parameters from paper for just a heartbeat
        a = 0.5;
        v1 = .97;
        v2 = -1;
        d = 3;
        e = 6;
        A = 2.5;
        w = 1.5;
        tspan = [0,30];

        %parameters for pacemaker
        T_p = 1.0; % pacing interval (s)
        x_th = .5; % nat heartbeat threshhold
        I0 = 10; % pacemaker pulse amp
        pulse_dur = 0.05; %pulse dur

        %just the heartbeat
        %ODE
        f_hb = @(t,X) [X(2);
        -a*(X(1)-v1)*(X(1)-v2)*X(2) - (X(1)*(X(1)+d)*(X(1)+e)/(e*d)) + A*sin(w*t)];

        % initial conditions
        X0 = [-0.1; 0.02];

        % solve
        [t1,X1] = ode45(f_hb,tspan,X0);
        figure;
        plot(t1,X1(:,1),'k'); grid on;
        title('Heartbeat Only (No Pacemaker)'); ylabel('x(t)');

        %pacemaker ODE system
        function dX = pacemaker_sys(t,X,a,v1,v2,d,e,A,w,Tp,xth,I0,pulse_dur)
        global last_beat t_stim %setting up our global var
        x = X(1);
        y = X(2);

        %detect our nat beat
        if x > xth && (t - last_beat) > 0.2
        last_beat = t;
        end
        %pacemaker pulse

        %plot pacemaker ver

        % ODE function - with pacemaker
        global last_beat t_stim
        last_beat = 0; t_stim = -999;

        f_pacemaker = @(t,X) pacemaker_sys(t,X,a,v1,v2,d,e,A,w,T_p,x_th,I0,pulse_dur);

        [t2,X2] = ode45(f_pacemaker,tspan,X0);

        plot_pacemaker_marks();
        title('Pacemaker Pulses'); ylabel('Pulse'); ylim([0 1.5])

        plot(t2,X2(:,1),'r'); grid on;
        title('Heartbeat with Pacemaker'); ylabel('x(t)'); xlabel('Time (s)');
```
---
##### Reference
[1] 	Yahalom, Asher & Puzanov, Natalia. (2023). “Feedback stabilization applied to heart rhythm dynamics with integro-differential equations method.” Research Square. July 4th, 2023   0.21203/rs.3.rs-2853196/v1. 

