---
title: "Research overview"
permalink: /research/
layout: single
author_profile: false
toc: true
toc_sticky: true
math: true
---

# <span style="display:none">Introduction</span>{: #intro}
The main aim of this project was to demonstrate torsional oscillations resulting from the transfer of angular momentum (AM) from light to matter without absorption and independent of whether the AM is spin or orbital in nature. To achieve this, we developed torsional micropendulums fabricated via direct laser writing (DLW) – a powerful, rapidly evolving additive manufacturing technique based on multiphoton polymerization under ultrafast laser illumination. In the context of AM-driven torsional oscillators, DWL is exceptionally versatile, as it enables precise engineering of the AM-converting component of the micropendulum – in our case, a transparent disk suspended on a thin wire at its center – for optimized optomechanical response to spin, orbital, or both types of AM. Since the seminal 1935 experiment by R. Beth [^beth1936] has already demonstrated torsional oscillations driven by spin AM of light using a macroscopic pendulum with a suspended retarder, our project focused on the complementary demonstration involving orbital AM. Specifically, we targeted the non-dissipative generation or conversion of an optical vortex beam, as originally proposed by L. Allen et al. in 1992 [^allen1992]. Despite its long-standing theoretical foundation, this phenomenon had not been experimentally realized until this work, where we designed and fabricated a micropendulum capable of being rotated by non-dissipative optomechanical transfer of orbital AM. The key component of the device is a spiral phase plate (SPP) with azimuthally varying thickness

$$
h(\phi) = \frac{\ell\lambda_{\rm pump}\phi}{2\pi(n-n_0)},
$$

where $\lambda_{\rm pump}$ is the working wavelength, $n$ and $n_0$ are the respective refractive indices of the disk material and the surrounding medium, and $\ell$ is an integer number called “topological charge”. Upon transmission through an SPP, every photon acquires an orbital AM of $\ell\hbar$ and the difference between the input and output AM produces torque on the disk. To measure the resultant angular deviation, we used a probe laser beam focused on the SPP step and sent to a calibrated quadrant photodetector (QPD). The method is detailed in the [Optomechanical experiment](#optomechanical-experiment) section below.

Noteworthy, it is also possible to repeat the original Beth experiment on spin AM with our device. For this, SPP should be replaced with a metasurface which converts polarization of the transmitted light due to form birefringence. As shown earlier [^varapnickas2021], such microstructures can be readily manufactured by DLW, and the probe method is still viable as it only requires a sharp relief feature near the disk edge. 


# Model
To establish the theoretical framework, we consider the torsional pendulum schematically depicted in Fig.1. The pendulum is represented by a horizontally oriented disk of radius $R$ and height $H$ suspended from its center on a thin cylindrical wire of diameter $D$ and length $L$. The disk is designed to perform a non-dissipative conversion of the total AM carried by an on-axis (that is, directed along the wire axis, $z$) beam of light, ${\mathbf{J}}_z$. Owing to the law of conservation of AM in the system, the difference in the AM of light,  $\Delta {\mathbf{J}}_z$, produces a nonzero torque $\Gamma_z$ on the disk, which thus rotates by an angle $\theta$ around $z$ axis until the driving torque is balanced by the elastic reaction of the wire.

<figure style="margin: 0 auto; display: table; text-align: center;">
  <img src="{{ 'assets/images/fig1_concept_250611.png' | relative_url }}" alt="Concept" style="width: 40%; height: auto;" />
  <figcaption style="margin-top: 0.5em;">Fig.1. Scheme of the torsional pendulum driven by non-dissipative conversion of AM of light.</figcaption>
</figure>

Assuming the linear regime (that is, $\Gamma_z\propto\theta$, which is true for small angular deviations, $\theta<10^{\circ}$), the equation of motion for this pendulum is

$$
\begin{align}
I\frac{d^2\theta}{dt^2} + \gamma_{\rm damp}\frac{d\theta}{dt} + K_1\theta = \Gamma_z(t), \tag{1}
\end{align}
$$

where $I$ is the moment of inertia of the suspended part of the pendulum along $z$ (neglecting the thin wire, $I \approx m_{\rm disk}R^2/2 = \rho\pi R^4 (H+h/2)/2$ with $\rho$ being the density of the disk material), $\gamma_{\rm damp}>0$ is the damping coefficient, and $K_1$ is the real part of the torsion constant defined as $K = K_1+iK_2$. In the elastic regime, the torsion constants of the wire can be found as $K_{1,2} = G_{1,2}\pi D^4/(32L)$, where $G_1$ and $G_2$ are the real and imaginary parts of the complex shear modulus, $G = G_1+iG_2$. In practice, the driving torque is sinusoidally modulated with an angular frequency $\omega$, and the magnitude $\Gamma_0$, as follows: $\Gamma_z(t) = \Gamma_0\cos\omega t$. Thus, we can rewrite Eq.1 in a more common form

$$
\begin{align}
\frac{d^2\theta}{dt^2} + 2\lambda\frac{d\theta}{dt} + \omega_0^2 \theta = F \cos\omega t, \tag{2}
\end{align}
$$

where $\lambda = \gamma_{\rm damp}/(2I)$, $\omega_0 = \sqrt{K_1/I}$ is the natural frequency of the pendulum, and $F=\Gamma_0/I$. In this project we are interested in the underdamped regime, $\lambda^2-\omega^2<0$, in which case the general solution of this linear differential equation is

$$
\begin{align}
\theta(t) = {\rm e}^{-\lambda t} \left(c_1 \cos(t\sqrt{\omega_0^2-\lambda^2}) + c_2 \sin(t\sqrt{\omega_0^2-\lambda^2})\right) + \theta_{\rm p}(t), \tag{3}
\end{align}
$$

where

$$
\begin{align}
\theta_{\rm p}(t) = \frac{F}{\sqrt{(\omega_0^2-\omega^2)^2 + 4\lambda^2\omega^2}}\cos(\omega t + \phi)
\end{align}
$$

is a particular solution, and

$$
\begin{align}
c_1 = -F\frac{\omega_0^2-\omega^2}{(\omega_0^2-\omega^2)^2 + 4\lambda^2\omega^2};\,\,\,\, c_2 = -F\frac{2\lambda\omega^2}{(\omega_0^2-\omega^2)^2 + 4\lambda^2\omega^2};
\end{align}
$$

$$
\begin{align}
\phi = -\arctan\left(\frac{2\lambda\omega}{\omega_0^2-\omega^2}\right). \tag{4}
\end{align}
$$

Once we let the pendulum stabilize ($t \gg 2\pi/\omega \sim 10$ µs in practice), Eq.3 loses the exponential term and we have the steady-state oscillating solution with the magnitude

$$
\begin{align}
\theta_{\rm dyn} = \frac{\Gamma_0}{I\sqrt{(\omega_0^2-\omega^2)^2 + 4\lambda^2\omega^2}} \tag{5}
\end{align}
$$

for the dynamic angular deviation.

We distinguish two contributions to the damping; external (energy dissipation due to friction with air) and internal (due to losses within the wire material): $\gamma_{\rm damp} = \gamma_{\rm ext}+\gamma_{\rm int}$. To assess the external part, let us calculate the Reynolds number, ${\rm Re} = \rho_0 v R/\eta$, where $\rho_0 = 1.2$&nbsp;kg/m$^3$ is the air density, $\eta=2\times10^{-5}$ Pa s is its dynamic viscosity, and $v$ is the maximum speed of the air flow near the disk. During the steady-state torsional oscillations at resonance, the maximum angular speed of the disk is $\omega_{\rm max}=\dot\theta_{\rm dyn}(0)=\theta_{\rm dyn}\omega$, and $v=R\omega_{\rm max} = R\omega\theta_{\rm dyn}$. With typical experimental values of $R=25$&nbsp;µm, $\omega\sim10^5$&nbsp;rad/s, and $\theta_{\rm dyn}\sim0.1$&nbsp;mrad, the Reynolds number is ${\rm Re}=\rho_0 R^2\omega\theta_{\rm dyn}/\eta<10^{-4}$. Following [^sanchez-padilla2020], we evaluate $\zeta {\rm Re}^2<10^{-11}$ (where $\zeta\sim10^{-3}$) and conclude that the hypothesis of creeping flow is valid and $\gamma_{\rm ext}=(32/3)\eta R^3$. Taking the internal losses as $\gamma_{\rm int} = K_2/\omega$, we have

$$
\begin{align}
\frac{\gamma_{\rm ext}}{\gamma_{\rm int}} = \frac{256\eta R}{3\pi D^2 G_2}\sqrt{\frac{L G_1}{\rho H}}. \tag{6}
\end{align}
$$

Preliminary fabrication tests suggested us to take the following values for the geometrical parameters of micropendulums: $R=30$&nbsp;µm, $H=3$&nbsp;µm, $L=50$&nbsp;µm, $D=4$&nbsp;µm <a id="geom"></a>
, which correspond to the natural frequency $f_0 = \omega_0/(2\pi)\approx 28$. Then Eq.6 gives $\gamma_{\rm ext}/\gamma_{\rm int}\approx 0.06$, hence we can neglect the external losses and assume $\gamma_{\rm damp} = \gamma_{\rm int}=K_2/\omega$, which gives $\lambda = K_2/(2I\omega)$. Then, dropping the subscripts for simplicity, we get from Eq.5

$$
\begin{align}
\theta = \frac{\Gamma_0}{\sqrt{(K_1-I\omega^2)^2 + K_2^2}}. \tag{7}
\end{align}
$$

The maximum angular deviation, $\theta_{\rm max}$, occurs at the resonant angular frequency $\omega_{\rm max,\,int}$ for which the denominator of Eq.7 is minimum. This happens when $\omega_{\rm max,\,int} = \sqrt{K_1/I} = \omega_0$, so for such oscillator the resonant frequency coincides with the natural frequency.

Let us introduce the normalized frequency, $\nu = f/f_{\rm max} = \omega/\omega_{\rm max,\,int} =\omega/\omega_0$, and the dimensionless parameter $\gamma=K_2/K_1$ associated with mechanical losses. Then we can write

$$
\begin{align}
\theta = \frac{\Gamma_0}{K_1\sqrt{(1-\nu^2)^2 + \gamma^2}},\,\,\,\,\,\,\,\,\,\, \theta_{\rm max} = \frac{\Gamma_0}{K_2} \tag{8}
\end{align}
$$

and in the normalized form:

$$
\begin{align}
\frac{\theta}{\theta_{\rm max}} = {\tilde\theta} =  \frac{\gamma}{\sqrt{(1-\nu^2)^2 + \gamma^2}}. \tag{9}
\end{align}
$$

The phase delay (Eq.4) between the pump and the mechanical signal can be expressed as

$$
\begin{align}
\phi = -\arctan\left(\frac{\gamma}{1-\nu^2}\right). \tag{10}
\end{align}
$$

The material parameter, $\gamma$, depends on the fabrication conditions and cannot be measured directly. Therefore, we express it in the terms of the measurable quality factor, $Q = f_{\rm max}/\Delta f$, where $\Delta f$ is the full width at the half-maximum of the spectrum, ${\tilde \theta}(f)$. From this definition of $Q$ we find

$$
\begin{align}
Q = \frac{1}{2\left( \sqrt{1+\gamma\sqrt{3}} -1\right)}. \tag{11}
\end{align}
$$

In practice, the measured spectra of the angular deviation magnitude, ${\tilde \theta}(f)$, and the phase delay, $\phi(f)$, are fitted to Eqs.9,10 with $\gamma$ linked to the quality factor according to Eq.11.


<!----------------------------------------------------------->
# Fabrication
Torsion micropendulums were fabricated by multiphoton 3D lithography using a well-established serial DLW technique [^brasselet2010] [^varapnickas2020], see the scheme in Fig.2. The working material was the silicon–zirconium hybrid photopolymer SZ2080 (without a photoinitiator to avoid burning by the pump laser beam), drop-casted on a glass cover slip and pre-baked successively at 40, 70 and 90$^{\circ}$ C for 20 minutes in each step. Two DWL systems were used: (i) custom one based on amplified laser Pharos (Light Conversion, Ltd.) with a second harmonic at 515&nbsp;nm wavelength, 300&nbsp;fs pulse duration, 200&nbsp;kHz repetition rate, 50&nbsp;µm/s writing speed and 0.04&nbsp;mW average power (pulse energy 0.20&nbsp;nJ); (ii) commercial Nanofactory workstation (Femtika) based on the femtosecond oscillator Flint (Light Conversion, Ltd.) with a second harmonic at 517±10&nbsp;nm, 144&nbsp;fs pulse duration, 76&nbsp;MHz  repetition rate, 100&nbsp;µm/s writing speed and 4.7&nbsp;mW average power (pulse energy 0.06&nbsp;nJ). In both systems the beam was focused through a 63x oil-immersion microscope objective lens (Plan Apochromat Zeiss) with a numerical aperture of NA = 1.4, thus producing intensities around 0.84&nbsp;TW/cm$^2$ and 0.68&nbsp;TW/cm$^2$ for the systems (i) and (ii), respectively.

<figure style="margin: 0 auto; display: table; text-align: center;">
  <img src="{{ 'assets/images/fig2_DLW_setup_240412.png' | relative_url }}" alt="DLW" style="width: 90%; height: auto;" />
  <figcaption style="margin-top: 0.5em;">Fig.2. Schematic of both DLW workstations. The femtosecond-laser beam is frequency-doubled by passing through a nonlinear crystal (NC), expanded through a telescope (not shown) to fill the aperture of a microscope objective (MO), and guided through the galvanometric scanning system (GS) to expose the sample fixed on the XY positioning stage (Aerotech) using a vacuum chuck and/or Kapton™ tape. The writing process is realized by the GS and/or the positioning stages (XY and Z), the laser shutter, and the attenuator (A), all controlled by the 3D Poli softwate. The MO is employed for both laser beam focusing and real-time sample imaging (by a CMOS camera) under red LED illumination in transmission through a long-pass dichroic mirror (DM). The writing power is set by A which is calibrated prior to each fabrication session using a removable photodetector (PD). A pair of lenses (L1, L2) in the 4F configuration relays the beam from GS to the back focal plane of MO for the linear beam stirring over the maximum field of view.</figcaption>
</figure>

The DLW process was controlled using 3D Poli software (Femtika) with a custom script to produce each microstructure layer by layer. To ensure smooth polymerization, the scanning was done with concentric circles for the wire, and concentric helices for the SPP. Fabrication of a single micropendulum structure took approximately 3 hours. After exposure, each sample was developed in acetone for 1 hour, rinsed in ethanol, and dried using critical point drying (CPD, Quorum K850) to minimize the damaging effects of surface tension on the wire and disk orientations. For inspection purposes, test samples were coated with about 20 nm of silver and imaged using a scanning electron microscope (SEM, Prisma E from Thermo Fisher Scientific). Typical images are shown in Fig.3(a-c), where the middle structure is the 'null' pendulum, which includes vertical steps (required for rotation detection) but lacks an SPP ramp and is therefore not expected to produce orbital AM conversion. The micropendulums had the parameters given [above](#geom), except the designed wire thickness which was set to $D = 2.7$&nbsp;µm because the fabricated wires were consistently measured to be thicker than the designed ones. The SPP step height $h = \lambda_{\rm pump} / (n - n_0)$, where $\lambda_{\rm pump}=532$&nbsp;µm, $n=1.504$ and $n_0=1$. are the refractive indices of the polymer and the surrounding medium (air), respectively. In the 'null' pendulum, the steps were designed to have the same height, $h \approx 1.055$&nbsp;µm. The driving torque was modeled as $\Gamma_0 = \ell \lambda_{\rm pump} P/(2\pi c)$, where $c$ is the speed of light in vacuum and $P$ is the intercepted optical power.


# Characterization
# Optomechanical experiment
# Results


[^beth1936]: R. A. Beth, “Mechanical Detection and Measurement of the Angular Momentum of Light,” Phys. Rev., vol. 50, pp. 115–125, 1936.
[^allen1992]: L. Allen et al., “Orbital angular momentum of light and the transformation of Laguerre-Gaussian laser modes,” Phys. Rev. A, vol. 45, pp. 8185–8189, 1992.
[^varapnickas2021]: S. Varapnickas, S. C. Thodika, F. Moroté, S. Juodkazis, M. Malinauskas, and E. Brasselet, “Birefringent optical retarders from laser 3D-printed dielectric metasurfaces,” Appl. Phys. Lett., vol. 118, no. 15, p. 151104, Apr. 2021.
[^sanchez-padilla2020]: B. Sanchez-Padilla and E. Brasselet, “Torsional Mechanical Oscillator Driven by the Orbital Angular Momentum of Sound,” Phys. Rev. Appl., vol. 13, no. 6, p. 064069, Jun. 2020
[^brasselet2010]: E. Brasselet, M. Malinauskas, A. Žukauskas, and S. Juodkazis, “Photopolymerized microscopic vortex beam generators: Precise delivery of optical orbital angular momentum,” Appl. Phys. Lett., vol. 97, no. 21, p. 211108, Nov. 2010
[^varapnickas2020]: S. Varapnickas, A. Žukauskas, E. Brasselet, S. Juodkazis, and M. Malinauskas, “3D microoptics via ultrafast laser writing: Miniaturization, integration, and multifunctionalities,” in Three-Dimensional Microfabrication Using Two-Photon Polymerization, I. Sakellari, Ed., Amsterdam, Netherlands: Elsevier, 2020, pp. 445–474

