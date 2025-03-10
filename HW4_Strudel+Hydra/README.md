# Homework 4
## Strudel + Hydra

- To start things off, I decided I wanted to use an amen break sample.
- So I scrolled around the examples until I found an example on Strudel called "Gothic Materialism and Cybernetic Theory-Fiction 2025 03 06" by Angel Jara.
- Here's what their code looked like.
```
//"Gothic Materialism and Cybernetic Theory-Fiction 2025 03 06"
//@by Ángel Jara
samples({ loopAmen02: 'https://cdn.freesound.org/previews/736/736476_16019844-hq.mp3' })
setcps(151/60/4)

await initHydra()
let pattern = "[ [[0!4] [0!4] [2!4] [1!4]]!3 [[2!4] [2!4] [1!4] [2!4]] ]/16"
solid([1,0,0],[0,1,0],[0,0,1])
  .mask(shape(4)) 
  .modulate(noise(H(pattern.mul(2))))
  .pixelate(20,20)
  .out(o0)




laBateria:
s("loopAmen02")
.fit().chop(32) 
// .hush()

elBajo:
stack(
  n(pattern)
  .scale("E1:minor:Pentatonic"),
    n(pattern)
  .scale("E3:minor:Pentatonic"),
)
  .s("sawtooth")
  .dist(3)
  .hpf(rand.range(100,1400).slow(4))
  .hpq("<0  <10!3 20>>/4")
  .legato(0.5)
  .ply(3)
  .mask("[1 0 1]*4")
// Em7 Am7 G Am7 G Am7
```
- After finding the example with the amen break, I just took the following code for the sample.
```
samples({ loopAmen02: 'https://cdn.freesound.org/previews/736/736476_16019844-hq.mp3' })
```
- Next I looked through the code along example for class from last week which looked like this
```
//Song :3
//By GMornin2U

//Kick <3
$: s("bd".segment(16).degradeBy(.7).ribbon(0,1))
  ._punchcard()

//Hehehe Snare Go BONK
$: s("sd").beat("4, 12",16)
  .sometimesBy(".3", x => x.ply("[2 | 4]"))
  ._punchcard()

//Simple Hi-Hat
$: s("hh!8")

//Bassline
$:n("0 0 0 0 5 5 5 5").segment(16).scale("Ab1:major").sound("gm_synth_bass_1")
  ._pitchwheel()

$:n("<Eb, Ab, C, G> <F, Ab, C, G>").sound("gm_pad_sweep")

//Funny Note Sequence
const seed = slider(0,0,24,1)
$: n(rand.range(0,12).segment(16).ribbon(seed,1)) .scale("Ab:major") .s("ocarina_small_stacc")
  .degradeBy(0.4).ribbon(0,1)._pianoroll()

```
- Then I just took the following code for my assignment.
```
const seed = slider(0,0,24,1)
$: n(rand.range(0,12).segment(16).ribbon(seed,1)) .scale("Ab:major") .s("ocarina_small_stacc")
  .degradeBy(0.4).ribbon(0,1)._pianoroll()
```
- So far here's what I got for this assignment.
```
samples({ loopAmen02: 'https://cdn.freesound.org/previews/736/736476_16019844-hq.mp3' })

$: s("loopAmen02")
.fit().chop(16)

const seed = slider(10,0,24,1)
$: n(rand.range(0,12).segment(16).ribbon(seed,1)) .scale("Ab:major") .s("triangle")
  .degradeBy(0.4).ribbon(0,1)._pianoroll()
```
- Right now, this feels satiafactory! However, I do want to be able to mess with the drum beat by glitching it out somehow.
-So I tweaked the code to make it work on the drums but I didn't like it.
- So I'm gonna make another note one, but for a bassline
- Here's what I have now!
```
samples({ loopAmen02: 'https://cdn.freesound.org/previews/736/736476_16019844-hq.mp3' })
const seed = slider(0,0,24,1)

//Drums
$: s("loopAmen02")
.fit().chop(16).ribbon(seed,1).ribbon(0,1)

//Bass
$: n(rand.range(-12,0).segment(16).ribbon(seed,1)) .scale("F#:major") .s("sawtooth")
  .degradeBy(0.2).ribbon(0,1)

//Lead
$: n(rand.range(0,12).segment(16).ribbon(seed,1)) .scale("F#:major") .s("triangle")
  .degradeBy(0.4).ribbon(0,1)._pianoroll()
```
- I wanna spice it up somehow so I wanna implement some reverb!
-After messing with the gain and adding reverb and distortion, this is what I ended up with!
```
samples({ loopAmen02: 'https://cdn.freesound.org/previews/736/736476_16019844-hq.mp3' })
const seed = slider(6,0,24,1)

//Drums
$: s("loopAmen02")
.fit().chop(16).ribbon(seed,1).ribbon(0,1)
  .distort("2")
  .room(1)
  .gain(.4)

//Bass
$: n(rand.range(-12,0).segment(8).ribbon(seed,1)) .scale("F#:major") .s("sawtooth")
  .degradeBy(0.2).ribbon(0,1)
  .distort("1")
  .gain(.4)

//Lead
$: n(rand.range(0,12).segment(16).ribbon(seed,1)) .scale("F#:major") .s("triangle")
  .degradeBy(0.4).ribbon(0,1)
  .room(1)
  .gain(1.5)
```
- Now I just need some visuals!
- For that I just kinda copied this example because I thought it was cool! I'm not the best at OG visual ideas but also I'm feeling a bit more simplistic.
```
await initHydra({detectAudio:true})
let pattern = "<3 4 5 [6 7]*2>"
shape(H(pattern)).repeat()
.scrollY(
  ()=> a.fft[0]*.25
)
.add(src(o0).color(.71 ).scrollX(.005),.95)
.out(o0)
n(pattern).scale("A:minor").piano().room(1)
```
- And the result is this!
```
samples({ loopAmen02: 'https://cdn.freesound.org/previews/736/736476_16019844-hq.mp3' })
const seed = slider(0,0,24,1)

//Drums
$: s("loopAmen02")
.fit().chop(16).ribbon(seed,1).ribbon(0,1).distort("2").room(1)
  .gain(.4)

//Bass
$: n(rand.range(-12,0).segment(8).ribbon(seed,1)) .scale("F#:major") .s("sawtooth")
  .degradeBy(0.2).ribbon(0,1).distort("1")
  .gain(.4)


//Lead
$: n(rand.range(0,12).segment(16).ribbon(seed,1)) .scale("F#:major") .s("triangle")
  .degradeBy(0.4).ribbon(0,1)
  .room(1)
  .gain(1.5)

await initHydra({detectAudio:true})
let pattern = "<3 4 5 6 7 8 9>"
shape(H(pattern)).repeat()
.scrollY(
  ()=> a.fft[0]*.25
)
.add(src(o0).color(.71 ).scrollX(.005),.95)
.out(o0)
```
- Thank u :3
