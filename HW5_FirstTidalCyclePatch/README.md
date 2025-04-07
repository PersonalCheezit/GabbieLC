# Homework 5
## First Tidal Cycles Patch

- To start things off, I looked at the class repository
- Specifically [this one](https://github.com/rdwrome/343sp25/blob/main/08tidalcycleseffects/README.md)
- Then I selected the following
```
d1 $ s "hh*16?" # djf sine

d1 $ s "wobble" # crush "[2 | 16]"
```
- Then I decided I needed a kick drum because I thought the hi-hat sounded cool
- So I took the xfade example, tweaked it and coded the following
```
d1 $ s "909*4"
```
I also wanted a snare drum so I added this 
```
d1 $ s "sd*2"
```
- Then I tried playing it but none of them were coming on simultaniously
- That's when I learned that in order to have that function, you change the number on the d (i.e d1, d2, d3, d4)
- Finally I needed to quiet things when I was finished making noises so I added a hush function
- Here's the final result!
```
d1 $ s "hh*16?" # lbrick sine

d2 $ s "909*4"

d3 $ s "wobble" # crush "[2 | 16]"

d4 $ s "sd*2"

hush
```



