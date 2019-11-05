# Differential Evolution (DE) Optimization with Python
A simple, bare bones, implementation of <a target="_blank" href="https://en.wikipedia.org/wiki/Differential_evolution">differential evolution optimization</a> that accompanies a tutorial I made which can be found here: https://nathanrooy.github.io/posts/2017-08-27/simple-differential-evolution-with-python/

## Installation
You can either download/clone this repo and use as is, or you can pip install it with the following command:
```sh
pip install git+https://github.com/nathanrooy/differential-evolution-optimization
```

## Usage
Once you have completed the installation, usage is similar to that of other common optimization frameworks.
```py
>>> from diffevo import de_simple
```
Next, you need to specify a cost fucntion. I included the sphere function for example purposes, but you'll probably end up using your own.
```py
>>> from diffevo.cost_functions import sphere
```
Lastly we need to specify some optimizer specific constants. For more information on what these values are and how best to use them, see the linked blog post at the top of this page.

```py
>>> bounds = [(-1,1),(-1,1)]            # bounds [(x1_min, x1_max), (x2_min, x2_max),...]
>>> popsize = 10                        # population size, must be >= 4
>>> mutate = 0.5                        # mutation factor [0,2]
>>> recombination = 0.7                 # recombination rate [0,1]
>>> maxiter = 20                        # max number of generations
```
Now, let's minimize this!
```py
>>> de_simple.minimize(sphere, bounds, popsize, mutate, recombination, maxiter)
```
The output of which should look close to this:
```py
...
GENERATION: 20
   > 2.6635635326983712e-05 [0.0018208872335391882, 0.004829079105763097]
   > 4.9580606970726694e-05 [0.0070407589280894346, 9.121780119916148e-05]
   > 2.2162273539063642e-05 [-0.003015611999457198, -0.003615018368942736]
   > 1.959970961017459e-05 [0.002787324055676138, 0.0034395543634057764]
   > 7.025341756207273e-05 [-0.0046121121033863045, -0.006998702701777687]
   > 3.5972219029065346e-05 [-0.0004056761521820749, -0.005983949021224704]
   > 2.4987227314433647e-05 [-0.002532393588388723, -0.0043097807401213965]
   > 3.358213318176877e-05 [0.0029016104781936065, -0.0050162525668676055]
   > 7.198803745771137e-06 [-0.00018143147319893155, 0.002676917325265015]
   > 1.577366384694402e-05 [0.0035989612612941646, -0.0016796254602285399]
      > GENERATION AVERAGE: 3.0574569012700424e-05
      > GENERATION BEST: 7.198803745771137e-06
         > BEST SOLUTION: [-0.00018143147319893155, 0.002676917325265015] 

```


