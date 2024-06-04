<section>

## Toward user-friendly ML in Fortran
<div style="display: flex; flex-direction: row;">

<div style="flex: 1; margin-top: 50px">

  <h3>My Fortran Book</h3>

  <ul> 
    <li>Learn modern Fortran from the ground up</li>
    <li>Practical, hands-on, science-oriented examples</li>
    <li>Published in Q4 2020</li>
    <li>3707 copies sold as of Q4 2023</li>
    <li>4.8 stars on Amazon</li>
    <li>Early draft of Chapter 6 implemented a neural network</li>
  </ul> 
</div>

<div style="flex: 1;">
  <a href="https://www.manning.com/books/modern-fortran">
    <img height=500 src="assets/modern-fortran-cover.png"></img>
  </a>
</div>

</div>

</section>


<section style="display: flex; flex-direction: column;">

<div style="flex: 8">

## neural-fortran: A parallel deep learning framework for Fortran applications

* Created to enable pure Fortran ML in Fortran applications
* Training and inference of arbitrarily deep dense and convolutional networks
* Optimizers: SGD, RMSProp, Adagrad, Adam, AdamW
* Data parallelism with Fortran 2018 collectives
* Used in over a dozen published studies from chemistry and combustion to weather and climate
* https://github.com/modern-fortran/neural-fortran

<div class="reference"><a href="https://doi.org/10.1145/3323057.3323059">Curcic (2019)</a></div>
</div>

<div style="flex: 2">
  <img height=90 src="assets/nasa.png"></img>
  <img height=60 src="assets/gsoc.png"></img>
</div>    
</section>


<section>

## Creating, training, and running a CNN with neural-fortran

```fortran
use nf
type(network) :: net

! Create the model
net = network([ &
  input(784), &
  reshape([1,28,28]), &
  conv2d(filters=8, kernel_size=3, activation=relu()), &
  maxpool2d(pool_size=2), &
  conv2d(filters=16, kernel_size=3, activation=relu()), &
  maxpool2d(pool_size=2), &
  dense(10, activation=softmax()) &
])

! Run training
call net % train( &
  training_images, &
  label_digits(training_labels), &
  batch_size=128, &
  epochs=10, &
  optimizer=adam(),
)

! Run inference
print *, net % predict(test_images)
```
</section>

<section>

## More Fortran ML goodness

* [inference-engine](https://github.com/BerkeleyLab/inference-engine) - A deep learning library for HPC applications
* [athena](https://github.com/nedtaylor/athena) - Another ML framework, inspired by neural-fortran
* [fastGPT](https://github.com/certik/fastGPT) - Fast GPT-2 inference in Fortran
* [llm.f90](https://github.com/rbitr/llm.f90) - Pure Fortran Llama2 inference
* [ferrite](https://github.com/rbitr/ferrite) - Simple, lightweight transformers in Fortran
</section>