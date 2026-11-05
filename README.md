# Cycling Climb Calculator

Web-based calculator to estimate the mean **power output (PO)** and **oxygen uptake (VO₂)** of a cyclist during a sustained climb from ascent time, elevation gain, distance and system mass.

**Use it online:** https://plvalenzuela.github.io/Cycling-calculator/

## How to use

1. Enter the rider's body mass and the mass of the bike and everything carried (clothing, shoes, helmet, bottles, devices).
2. Enter the ascent data: ascent time (mm:ss or h:mm:ss, from the start to the summit, excluding stops), elevation gain, distance and mean altitude of the climb (average of start and summit altitudes).
3. Adjust the model parameters if needed (tyre rolling resistance and gross efficiency).
4. Optionally, enter a measured power output (VO₂ is then estimated from this value) or a known CdA (it then replaces the body-mass-based estimate).

The calculator shows the estimated PO (W and W/kg), the estimated VO₂ (ml/kg/min and L/min), the range of VO₂ values obtained when gross efficiency varies by ±1%, the expected individual error of the estimates, and the contribution of gravity, aerodynamic drag and rolling resistance to the estimated PO. A warning is shown when the input data clearly depart from the conditions under which the model was validated (average gradient <4% or effort duration <5 min).

## Model

**Power output.** Mean PO is estimated as the sum of the gravitational (P<sub>g</sub>), aerodynamic (P<sub>a</sub>) and rolling resistance (P<sub>r</sub>) components, divided by a drivetrain efficiency of 96%:

- P<sub>g</sub> = m · g · a / t
- P<sub>a</sub> = ½ · ρ · C<sub>d</sub>A · v³
- P<sub>r</sub> = C<sub>rr</sub> · m · g · v

where *m* is total system mass (rider plus bike and gear, kg), *g* = 9.81 m·s⁻², *a* is elevation gain (m), *t* is ascent time (s), *v* is mean climbing speed (distance/time, m·s⁻¹) and C<sub>rr</sub> is the coefficient of rolling resistance.

- Aerodynamic drag assumes still air. Unless a known CdA is entered, the projected frontal area (A<sub>p</sub> = 0.04324 · m<sub>b</sub><sup>0.594</sup>) and drag coefficient (C<sub>d</sub> = 4.45 · m<sub>b</sub><sup>−0.45</sup>) are estimated from body mass (m<sub>b</sub>) using allometric equations for the brake-hoods position (Heil, 2001, 2002).
- Air density is estimated from mean altitude (*h*) with the barometric formula: ρ = 1.225 · e<sup>−h/8500</sup>.

**Oxygen uptake.** PO is converted to energy expenditure assuming the selected gross efficiency (default 21%), and then to VO₂ assuming an energy equivalent of 5.189 kcal per litre of O₂, corresponding to a respiratory exchange ratio of 1.0. This is appropriate for high-intensity efforts; for submaximal or low-intensity exercise, where fat oxidation is higher, this assumption may slightly underestimate the actual VO₂. VO₂ is expressed relative to rider body mass.

## Validity and limitations

The model was validated in trained male cyclists during a sustained, evenly paced, individual uphill time trial (9.2 km, ~7% average gradient, ~30 min, low wind). In that study, estimated PO showed a trivial bias with individual differences of about ±6.5% (95% limits of agreement), and VO₂ estimates showed individual differences of about ±13–14%. Estimates are therefore more suitable for group-level comparisons or for estimating the order of magnitude of a performance than for detecting small changes in a single rider.

Accuracy is expected to decrease on shallower climbs, in windy conditions, when riding in a group (drafting), with variable pacing, or in short efforts. As gravity accounts for most of the power on steep climbs, system mass, elevation gain and ascent time should be measured rather than assumed: an error of 1 kg, 10 m or 30 s changes the estimated PO by roughly 1–2%. Each 1% (absolute) error in gross efficiency changes the estimated VO₂ by ~5%.

## How to cite

Sitko S, Romero-Parra N, Benito-Peinado PJ, Peinado AB, Valenzuela PL. Validity of mathematical model estimations of power output and oxygen uptake during a sustained uphill time trial: a preliminary field-based study in trained cyclists. *Int J Sports Physiol Perform* (under review).

## References

- Heil DP. Body mass scaling of projected frontal area in competitive cyclists. *Eur J Appl Physiol*. 2001;85(3-4):358-366.
- Heil DP. Body mass scaling of frontal area in competitive cyclists not using aero-handlebars. *Eur J Appl Physiol*. 2002;87(6):520-528.
- Péronnet F, Massicotte D. Table of nonprotein respiratory quotient: an update. *Can J Sport Sci*. 1991;16(1):23-29.

## License

Apache-2.0 (see [LICENSE](LICENSE)).
