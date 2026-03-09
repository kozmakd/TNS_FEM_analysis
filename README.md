# Dataset Title

[Access this dataset on Dryad](doi.org/10.5061/dryad.k3j9kd5mg)

This dataset contains FEM simulations in COMSOL to illustrate the activation function at anatomical depths relevant to the supraorbital, infraorbital, and mental nerve branches in human donors (.mph). Anatomical data (.xlsx) and as python code (.ipynb) to generate figures are included.

## Description of the data and file structure

A FEM computational model was developed to illustrate sensitivity of on-target fibers (trigeminal nerve branches) versus off-target fibers (cutaneous nociceptors). The activating function (AF), a proxy for nerve fiber engagement, was used to characterize how the spatial distribution of the extracellular field from TENS stimulation influences activation of unmyelinated nociceptor fibers that run parallel to the skin surface, as well as to illustrate nerve fiber engagement within the SON, ION, and MN nerve trunks. A quasistatic electric currents (EC) model was created in COMSOL 6.2 using the AC/DC EC module to solve for the electric potential within a three-layered homogeneous volume conductor under bipolar stimulation.

We isolated a 2D plane within the 3D geometry informed by Verma et al 2021a, cutting orthogonally through skin, adipose, and muscle. We simplified this 3D model to a 2D model within COMSOL to focus computational resources on the cutaneous and nerve trunk evaluation lines. A highly conductive copper electrode with uniform current density was used to represent the TENS voltage source. A lumped stratum corneum impedance layer was modeled between the TENS contacts and the skin, with a thickness of 20 µm and a permittivity equal to that of the skin. A sensitivity analysis of stratum corneum impedance was performed, set at one and two orders of magnitude greater and less than that of the skin, as well as its thickness, which ranged from 10 to 30 µm in 5 µm increments. This lumped layer was intended to simulate the effects of increased impedance due to layers of dead skin and sweat glands increasing local electrolyte concentration within the stratum corneum. Since noninvasive stimulation involves variable electrode conformance and limited compliance to deliver the necessary current, voltage-controlled stimulation was utilized in the model. Bipolar voltage sources of ±15 V were applied to the upper surfaces of the TENS copper discs. The lateral edges of the model, spanning the skin, adipose, and muscle layers, were assigned as ground, while all other external surfaces, including the skull, were treated with no-flux boundary conditions to simulate high-impedance barriers. Current conservation boundary conditions were applied throughout the continuous TENS-tissue domains. Resulting second order spatial derivatives of the extracellular potentials along these nerve evaluation lines (the activation function) were exported and plotted in python.


## Sharing/Access information

This data supports this publication

[Publication](doi.org/10.1088/1741-2552/ae1dae)

The following data files to support this publication are available here on Dryad:

[Dryad Data Files](doi.org/10.5061/dryad.k3j9kd5mg)

(1) **Comsol_OUTPUT_(submission).xlsx** - output from COMSOL with the maximum values of the activation function for different depths, varying skin impedance properties.

Branch =  Trigeminal Nerve Branch (V1 indicates the V1 branch of the nerve including the supraorbital nerve)
Contact Conductance (S/m)	=  		Conductance of the Thin Impedance Layer in FEM Model
Barrier Distance (um) =  Barrier distance (in microns). Distance between electrode contact and the upper skin layer. Representative impedance layer for the stratum corneum.
Nociceptor AF (V/m^2)	=  	Activation function proxy for a cutaneous depth. Second order spatial derivative of the extracellular potential along the  an unmyelinated fiber parallel to the surface of the skin.
Nerve AF (V/m^2)	=  	Activation function proxy for a nerve trunk depth. Second order spatial derivative of the extracellular potential along the  an unmyelinated fiber parallel to the surface of the skin.

(2) **FEM_Analysis_Script.ipynb** - Jupyter Notebook script to generate plots from 'Comsol_OUTPUT_(submission).xlsx'. This script reads in data from a sensitivity analysis across 'Contact Conductance' and 'Barrier Thickness' and generates figures illustrating the relative behavior of the second order difference for the extracellular potential for generalized unmelinated fibers (V/m^2).

(4) **Trigeminal_raw_data.xlsx** - COMSOL file for analyzing the activation fuction at anatomically relevant tissue depths

Donor	=  Human Cadaver ID
Nerve	=  Trigeminal nerve branch (SoN = supraorbital nerve, IoN = Infraorbital Nerve, MN = Mental Nerve)
L/R =  Left/Right
Total Area (um2) =  Squared microns of total nerve and fascicular tissue in each histology sample
Number of Fascicles =  Count of fascicles within each nerve sample
Area Fascicle (AF .. n) =  Squared microns of fascicular tissue for each individual segmented fascicle. Each row indicates a different nerve with subsequent columns being fascicles within that nerve.
Total Fascicular Area (um^2)=  Squared microns of fascicular area total. (Sum of all fascicles)
Connective Tissue Area (um^2) =  Squared microns of connective tissue area total. (Sum of all fascicles)
Distance from Midline (mm) - Distance from the midline in the skull to the foramen in each nerve.
Depth from Skin (mm) - Depth of each nerve sample relative to the upper surface of the skin at the foramen in each nerve.
Length x Width (mm) - Length and width of each trigeminal nerve sample.


## Code/Software

FEM_trigeminal_model.mph

[Access this COMSOL file on GitHub](https://github.com/kozmakd/TNS_FEM_analysis) using COMSOL 6.2. Note this raw COMSOL file requires an active license. Readable data is available above in **Comsol_OUTPUT_(submission).xlsx**

FEM Models were simulated in COMSOL 6.2 and resulting activation function maxima and sensitivity analyses were plotted using python 3.10 with jupyter notebook.