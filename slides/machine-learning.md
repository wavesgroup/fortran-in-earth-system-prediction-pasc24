<section>

## Machine Learning for Earth System Modeling
</section>


<section>

> "Software is eating the world..." </br> - Marc Andreessen, 2011</br>
<img src="assets/marc-andreesen.png" width="100">

> "...but AI is going to eat software." </br> - Jensen Huang, 2017</br>
<img src="assets/jensen-huang.png" width="100">
</section>


<section>

## ...and so it eats the Numerical Weather Prediction (NWP) as well

* We've entered a new revolution in NWP.
* AI NWP models are:
  - orders of magnitude faster;
  - match or beat the accuracy of traditional models on _some_ metrics
* New AI models appear rapidly: FourCastNet, GraphCast, PanguWeather, FuXi, NeuralGCM, AtmoRep, ClimaX, STORMER, ACE etc.
* We saw a tour de force of AI NWP models here at PASC24 on Monday
</section>


<section>

## Discussion from PASC24 session on AI NWP models on Monday

Q: "When will AI models completely replace traditional models?"

<p class="fragment">
A: "They won't."
</p>

<p class="fragment">
<i>Why? Because Earth scientists still need physics-based models to better understand and model the unresolved processes.</i>
</p>

</section>


<section>

## Traditional vs. ML-based NWP

* In traditional models, we ask: How to model the physical process that takes `x(t)` to `x(t+∆t)`?
 
* In ML-based models, we ask: What values of `w` in `matmul(w,x)` best map `x(t)` to `x(t+∆t)`?

$\rightarrow$ A key idea is that any process or data mapping can be modeled with a `matmul`.
</section>


<section>

## The two-language problem:
## Fortran ESM + Python ML

* Virtually all Earth System model components are written in Fortran:
  - Weather: [CAM](https://www.cesm.ucar.edu/models/cam), [GEOS](https://github.com/GEOS-ESM), [GFS](https://github.com/NOAA-EMC/fv3gfs), [ICON](https://gitlab.dkrz.de/icon/icon-model), [IFS](https://www.ecmwf.int/en/forecasts/documentation-and-support/changes-ecmwf-model), [MPAS](https://github.com/MPAS-Dev/MPAS-Model), [ModelE](https://www.giss.nasa.gov/tools/modelE/), [WRF](https://github.com/wrf-model/wrf)...
  - Ocean: [ADCIRC](https://github.com/adcirc/adcirc), [FVCOM](https://github.com/FVCOM-GitHub/FVCOM), [HYCOM](https://github.com/HYCOM), [MITgcm](https://github.com/MITgcm/MITgcm), [MOM](https://github.com/mom-ocean/MOM6), [NCOM](https://www.ncei.noaa.gov/products/weather-climate-models/global-navy-coastal-ocean), [NEMO](https://forge.nemo-ocean.eu/nemo/nemo)...
  - Waves: [SWAN](https://gitlab.tudelft.nl/citg/wavemodels/swan), [UMWM](https://github.com/umwm/umwm), [WAM](https://github.com/ecmwf-ifs/ecwam), [WaveWatch III](https://github.com/NOAA-EMC/WW3)...

* Meanwhile, mainstream ML are Python frameworks: [PyTorch](https://pytorch.org/), [TensorFlow](https://www.tensorflow.org/), [JAX](https://github.com/google/jax)

<div class="fragment">
$\rightarrow$ Domain scientist asks: How do I run ML within my Fortran application?
</section>


<section>

## Multiple approaches to ML in Fortran

* PyTorch bindings: [pytorch-fortran](https://github.com/alexeedm/pytorch-fortran), [ftorch](https://github.com/Cambridge-ICCS/FTorch), [torchfort](https://github.com/NVIDIA/TorchFort)
* TensorFlow bindings: [fortran-tf-lib](https://github.com/Cambridge-ICCS/fortran-tf-lib)
* _Pure Fortran ML_:
  - Naturally great fit for ML: First-class multi-dimensional arrays, `matmul`, `dot_product`, `sum`, `pack`, `unpack`, `reshape` etc.
  - Fast linear algebra libraries
  - No complexity associated with multi-language applications
  - Many Fortran programmers would love to use pure Fortran ML.
</section>