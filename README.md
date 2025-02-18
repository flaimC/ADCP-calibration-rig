# ADCP-calibration-rig
This repo documents the design and build of an ADCP calibration rig for a Nortek Signature 100. The rig utilizes syntactic foam and a large footprint to stay afloat and stable in a calibration tank. It is designed to be lifted with an over-head crane while the ADCP is attached. Future versions of this calibration tool will include lasers, cameras, and motorized ball movement to expidite the calibration process.
![adcpCalibrationRigAssy (3)](https://github.com/user-attachments/assets/6682834f-5ccf-42f9-8efa-a0ea38b2a108)



# Onshape CAD
This project was designed in a browser-based CAD program called Onshape. The document for this project can be found [here](https://cad.onshape.com/documents/10602cede9c07e59b6c9bb3e/w/70dcfadde18bdff9054825df/e/5ac3f072fa41a360b08c238f)

# ADCP calibration rig buoyancy calculation
### using Archimedes principle 
Archimedes principle states that the buoyancy of an object is equal to the mass of the water it displaces.

The buoyancy force of a fully submerged object is described as $F_B = V_{disp} \times \rho \times g$, where $V_{disp}$ is the displaced volume, $\rho$ is the density of the dsiplaced fluid, and $g$ is the gravitational constant.

We can expand on this equation to include the force of gravity acting upon the submerged object.

$$F_B = V_{disp} \times (\rho_{disp} - \rho_{object}) \times g$$

We can expand this equation and cancel out the gravitational constants to find the maximum mass a submerged volume of known density can support before being fully submerged.
$$M_{max} = V_{disp} \times (\rho_{disp} - \rho_{object})$$
For complex objects and geometries, the forces acting upon subcompenents need to be accounted.

$$M_{max} \times g = \left( \sum_{i=0}^n M_{i} \times g \right)$$
#### Define variables
Let,
$$B = \text{resultant maxium mass from chosen materials and volumes that can be supported without sinking},$$

$$\rho_{sw} = \text{assumed density of seawater in tech tank},$$
$$\rho_{syn} = \text{density of macrofoam-18 syntactic foam},$$
$$\rho_{hdpe} = \text{density of HDPE platstic sheet},$$
$$\rho_{misc} = \text{average density of submerged metal parts},$$

$$V_{syn} = \text{volume of syntactic foam},$$
$$V_{HDPE} = \text{volume of the HDPE sheet},$$
$$V_{misc} = \text{volume of submerged metal parts},$$

$$M_{ADCP} = \text{weight of ADCP in water},$$
$$M_{topmisc} = \text{weight of in-air metal parts}.$$
Note: The distrubtion of density variation does not matter for $\rho_{misc}$ since we are just looking for a buoyancy force, not stability. This density is calcuated from the total mass and volume of submerged metal parts (e.g., screws, nuts, rods).

#### Find the buoyancy
A buoyancy force is only calculated for submerged objects. The full mass of in-air objects is subtracted from the total bouancy. The top of the ADCP is not submerged, but the weight is nearly wholely contained at the bottom of the ADCP, so we are assuming the in-air weight of the top two-inches of the ADCP is negligible. Surface tension is also assumed to be negligible in this calculation.

$$B = V_{syn}(\rho_{sw}-\rho_{syn}) + V_{hdpe}(\rho_{sw}-\rho_{hdpe}) + V_{misc}(\rho_{sw}-\rho_{misc}) - M_{adcp} - M_{topmisc}$$

If $B > 0$, then the ADCP calibration rig should float. If $B < 0$, then the ADCP calibration rig should sink.

Given,

$$\rho_{sw} = 1035\text{ kg•m}^{-3},$$
$$\rho_{syn} = 290\text{ kg•m}^{-3},$$
$$\rho_{hdpe} = 941\text{ kg•m}^{-3},$$
$$\rho_{misc} = 3910.26\text{ kg•m}^{-3},$$

$$V_{syn} = 0.05968\text{ m}^3,$$
$$V_{HDPE} = 0.00509\text{ m}^3,$$
$$V_{misc} = 0.001306\text{ m}^3,$$

$$M_{ADCP} = 13\text{ kg},$$
$$M_{topmisc} = 4.8144\text{ kg}.$$

We can plug these values into our buoyancy equation and find the maximum in-air weight the calibration rig can hold before being completely submerged.

$$B = 0.05968 \text{ m}^3(1035 \text{ kg•m}^{-3}-290\text{ kg•m}^{-3}) +$$ 
$$0.00509\text{ m}^3(1035\text{ kg•m}^{-3}-941\text{ kg•m}^{-3}) +$$ 
$$0.001306\text{ m}^3(1035\text{ kg•m}^{-3}-3910.26\text{ kg•m}^{-3}) - 13\text{ kg}- 4.8144\text{ kg}$$

$$B=23.37 \text{ kg}$$

# Disclaimer
This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an ‘as is’ basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.
