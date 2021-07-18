# Tuning Manifold Charting: the Official Code Base for the Manifold Paper: 


## Dataset Structure
Our formatted and reduced dataset is stored in `.mat` format as a structure array, which can be accessed from Matlab or Python. 

* Each experimental session has one struct corresponding to Evolution, and one struct corresponding to Manifold experiment. 
* Array is organized in the order of experiment time for each monkey. 

## Code Structure
Our code is written in Matlab and Python. Matlab for most statistical analysis of *in vivo* data, Python esp. pytorch for the *in silico* experiment and modelling.

### Deep neural networks `DNN`
We curated a library of deep neural nets classes to use in our analysis, some implemented in matlab, some interfaced with pytorch implementation. These classes are used both in online experiments and analysis. 

### Black box optimization algorithms `optimizers`
We open source our adaption of ``Cholesky-CMA-ES` optimization algorithms, and the `ZOHA_Sphere` algorithms for the constrained optimization on the hyper-surface of a sphere. 

Test and demo code, to be added. 

### Experimental Control `experiment_ctrl`
Our experiments are controlled by custom Matlab script using Monkeylogic, with the image generator in matlab. The manifold image explorations are generated by Python / matlab after the Evolution finish. 

### Statistical Analysis `analysis`
* Receptive field mapping. 
* Evolution trajectory, successfulness, best generation. 
* Single Tuning Map Characterization
	* Tuning Map, basic stats (ANOVA, F statistics).
	* Kent function fitting of tuning map, extract Kent parameters. (`analysis\Kent_func`)
	* Non-parametric statistics of tuning maps: Volume under the Surface (VUS), Peak location
	* Population analysis `Manif_Map_Stat_Pop_Synopsis.m`
* Radial Tuning Curve analysis
	* Image distance matrix using LPIPS and various image distance measure.
	* Radial Tuning curve over several different spaces; AUC for tuning curve. 
* Tuning Map Similarity
	* Geometry of electrode organization. 
	* Measuring tuning map similarity by functional correlation on manifold
	* Tuning map similarity as a function to cortical distance 

### Plotting `visualization`
Some of our specialized plotting function
* Plot single tuning maps with colored framed image / color maps.(Figure 2B)
* Plot multiple tuning maps in an montage.(Figure 3A,5A)
* Plot radial tuning curves.(Figure 2D)
* Summarize score trajectory during Evolution (Figure 3F)
* Plot tuning maps in the same configuration as the electrode array. (Figure 5)

Other more generic plotting functions (inspired by `Seaborn` library in Python)
* Violin plot (wrap around [Violinplot-Matlab](https://github.com/bastibe/Violinplot-Matlab))
* Paired stripe plots, stripe plots with masks. 
