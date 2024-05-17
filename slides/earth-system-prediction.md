<section>

## What do we mean by _Earth System Prediction_?

* Earth comprises a complex system of interacting components, i.e. fluids, solids, ecosystems, and human societies
* Atmosphere, ocean, land, and ice
* Weather vs. climate
* Variety of scales: from seconds to millennia
* Interaction between components is key
* Virtually all models used today in research and operations are written in Fortran
</section>


<section>

## What do _I_ mean by _Earth System Prediction_?

* Atmosphere <-> Ocean surface waves <-> Ocean circulation
* Virtually 
</section>


<section>

## Richardson's forecast factory (1922)

* Weather Prediction by Numerical Process, by L.F. Richardson, Cambridge University Press, 1922
* TODO artistic renditions

</section>


<section>

## What's in a typical weather prediction model codebase?

* Some BLAS and LAPACK, likely inserted directly into the code rather than linked to as libraries
* Some FFT library, ditto, inserted rather than linked to
* Domain specific physics code, e.g. radiation, convection, turbulence, etc.,
  written in various dialects of Fortran, from pre-FORTRAN 77 to Fortran 90, with
  some more recent Fortran features sprinkled in here and there
* Both fixed-form and free-form source files.
* MPI calls for halo exchange at each time step
</section>


<section>

## The blessing and curse of Fortran

* Can't live with it, can't live without it
* Modern workforce is not trained in Fortran, but is thrown in with a "you'll figure it out"

</section>