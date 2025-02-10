# Homework 2
## Strudel Patch
- For this homework, I tried to make a drum beat.
- First I needed a base to start making the drum beat on Strudel.
- So I went onto [the class Github](https://github.com/rdwrome/343sp25/tree/main/01introtostrudel) and I messed with this example as a base!
```
// strudel
stack(
  "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] ",
).s()
```
- Then I removed all the drum sounds until I got a blank slate, which ended up looking like this.
```

stack(
  "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] ",
).s()
```
- Then I had to figure out a drum beat!
- Here's what I ended up with!
```
stack(
  "[bd ~ ~ ~] [~ ~ ~ bd] [bd ~ ~ ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [sd ~ sd ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  "[hh ~ hh ~] [~ ~ hh ~] [hh ~ hh ~] [~ ~ hh ~] ",
  "[~ ~ ~ ~] [oh ~ ~ ~] [~ ~ ~ ~] [oh ~ ~ ~] ",
).s()
```
- enjoy :)