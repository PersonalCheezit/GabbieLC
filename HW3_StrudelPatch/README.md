# Homework 3
## Strudel Patch 2

- For this strudel patch I started off by using the following example from the class as a base
```
n(rand.range(0,12).segment(8)) .scale("C:major") .s("sine")
```
- Afterwards I started messing with the parameters until I got something like this
```
n(rand.range(-12,24).segment(21)) .scale("F#:major") .s("triangle").slow(rand).degradeBy(0.4)
```
- I left it alone for a few days until I saw it again, made a change to the key and mode
```
n(rand.range(-12,24).segment(21)) .scale("Ab:lydian") .s("triangle").slow(rand).degradeBy(0.4)
```
- Now I want to add a sample or a drum beat and/or a sample but I need to figure out stacks.
- The I went on to [this specific strudel site](https://strudel.cc/learn/factories/) for some tips n tricks to combine some stuff and I landed on the following example!
```
s("hh*4").stack(
  note("c4(5,8)")
)
```
- So I added it a lil into my code and I ended up with the following
```
s("hh!4 ~ ").stack(n(rand.range(-12,24).segment(21)) .scale("Ab:lydian") .s("triangle").slow(rand).degradeBy(0.4))
```