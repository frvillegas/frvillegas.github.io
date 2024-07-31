Dec 5, 2018
-----------

Fernando Rodriguez Villegas (ICTP)

In this talk we will discuss the puzzle Blet. Its simple appearence
hides some interesting mathematics involving the geometry of certain
lattice paths in the plane and the group SL(2,R). It is also a nice
illustration of a typical discrete minimization problem where greed is
not the answer.

https://www.youtube.com/watch?v=1LTnBP2Asvs

Transcript (youtube --> ChatGPT)

Presenter: Well, welcome everyone. It's a pleasure for me to introduce 
Fernando. He will talk about a mathematical puzzle.

FRV: Thank you. So, this is a puzzle that I worked on many years ago
with two of my colleagues at the time at UT Austin, Lorenzo Sadún and
Felipe Voloch. And if you're curious about the name you see there, my
daughter Malena has been thanked for providing the name. It's a
complicated story why that happened.

FRV: This puzzle, with my colleagues at the time, made it to the
website puzzles.com. They even made this little logo. But anyway, what
I'd like to tell you is some mathematics that's behind it. This was
part of a course that I taught in Austin, where, with the excuse of
discussing various puzzles, I discussed some mathematics behind
them. So this is one, probably the more sophisticated in the sense of
what mathematics it involves.

FRV: Let me first tell you what the puzzle is. You start with a
sequence of pairs, A and B, arranged in a circle. Say, N is the number
of A's and B's. It’s going to be an even number, and this is the
starting configuration. There are two rules that you can use: if you
see a pattern of the form ABA, then you can change it to the pattern
BAB, and conversely, if you see the pattern BAB, you can change it to
ABA. These are the allowable moves. The goal is to maximize the number
of A's or maximize the number of B's, or minimize either one, because
it's all very symmetrical.

FRV: There's a clear direction in which it goes towards your goal. If
you see a pattern of the form BAB, this has only one A, and if you
change it to the pattern ABA, now you have two A's. So this direction
is the greedy direction that will increase the number of A's.

FRV: This puzzle, I don't think, or claim, to be particularly
interesting in itself. I mean, if you try it on your own a little bit,
you might find it interesting, but unfortunately, that would mean I
couldn't give the talk, so I'll spoil the little fun there might be
and tell you what's behind it myself. But it's an illustration of this
problem that greed is not the answer, typically.

FRV: We have an implementation that I’m not sure I'll be able to show
you right now. So, in the implementation, let's say N equals 28. You
click on such a pattern on the B, and it converts it into this, or you
click on this pattern on the A, and it gets you the other one. So
that's an implementation of this idea. If you're greedy, you only get
the number of A's to go up to 21, but in fact, the maximum possible is
23.

FRV: So let me just say a little bit about the type of problem. First
of all, I don't know if you've seen, you must have seen something like
this. This is peg solitaire. This is sort of a similar type of
idea. So you can say that these puzzles all involve replacing a
pattern with another one following specific rules.

FRV: So if you think of peg solitaire, A corresponds to pegs in blue,
and B is a blank. You can move this peg over to the blank and take
this blue one in the middle out. So it goes from BAA to BB, but in
this puzzle, you only go in one direction; you can't go back once you
do a move. And here, the goal is also similar: to minimize the number
of A's, which would be the number of blue pegs.

FRV: In this game, you can actually achieve one, and it's one of those
things that I played when I was a kid, about ten, and I managed to
solve it. Then later on, I got interested in this type of connection
between mathematics and puzzles. I even had a book by John Conway of
Cambridge, who's famous in many aspects, and one of them is his
interest in this type of stuff. He wrote a really nice book, which I
refused to read until I could solve the puzzle again, and I just never
could. So, progress doesn't seem to always go with age.

FRV: So the general picture here is that we have some kind of space of
configurations, which is typically very big. Even something like this,
I haven't been able to recall how many configurations are possible,
but it's a large number. And we're navigating through this to try to
minimize some function.

FRV: We're trying to minimize a function on a discrete space, and
that's a difficult problem. There's no calculus here to help us. So
let me just say a little bit about the question of minimizing discrete
functions. When I first started with this puzzle, I used this method
to try to understand what was happening before we eventually found a
solution.

FRV: Typically, if you have a problem of this kind, there wouldn't
necessarily be a way to solve it completely, which is what we have in
this case, which is the topic of the talk. But let me take a
parenthesis and discuss very superficially this question of maximizing
or, let's say, minimizing a discrete function. By that, I mean you
have a large discrete set and some function on that set that we want
to find a minimum value of.

FRV: To just schematically illustrate, let's think of the X variables,
which are the possibilities in our space, as a one-dimensional
thing. If you think of this as some big space, and then we have a
function, which from the point of view of physics would be energy, and
the graph may look like this, and what we're trying to do is find the
minimum values or one minimum value. Let's say it's only one, so we're
trying to reach this point by moving in this space.

FRV: If you start at some point, maybe the point is given to you, and
this is where you should start. So what you could do is,
schematically, think of the state that you're at as X0 here. Then you
make some move towards a neighboring point, which you could do perhaps
randomly. What you do is you compare the energy at the neighboring
point and the energy at the point you're at. If the energy at the
neighboring point is smaller than the one you're at, then you're happy
because that's a better point, so you take it.

FRV: And now the question becomes, what happens if the point that you
pick is actually worse? If you're greedy, you always want to go down,
and you will only take it in this case. In this case, you just don't
take it and try a new one. So what happens with that idea of being
greedy is that, for example, if you start here and you keep moving,
then you're going to get stuck at this point.

FRV: So, being greedy may result in getting stuck at local minima.

FRV: You can only change this pattern to this one, or backwards. In
the other game, you only find the peg correctly and just do the moves
the way I illustrated. If you have two blues with a space ahead, then
you can move one peg over the other one and remove the one in the
middle. That's all you can do; you can do it horizontally or
vertically. The idea is every time you do this, you have one less peg,
and you have to keep doing this, and the goal is to get to just one
peg at the end, which, of course, you cannot take because there's no
other move possible.

FRV: The issue here is we have a space of possibilities.

Audience member: Are they random?

FRV: No, you take a neighboring point; the move is something
reasonably close by. You do a small modification of your problem, like
here, you can think of this as a huge circle, and you do a tiny
modification to move to a neighboring configuration.

FRV: The idea from physics, resulting in an algorithm in a sort of
vague sense, not too specific, got the name of simulated
annealing. When you anneal, you heat a metal to a high temperature and
let it cool very slowly. The heating frees the atoms to do whatever
they want, and the cooling lets them sit and arrange themselves in a
better way than before. Very simply explained, you do something
similar here. The idea is, if we have an advantage, we take it, but if
there's a disadvantage, we take it with a certain probability. So, in
a certain sense, you flip a coin.

FRV: And you say, "Okay, look, this looks like a bad move, but I'll
take it anyway." And so, if you're stuck at this local minima, then if
you allow yourself to take some steps in the sort of wrong direction,
maybe you will climb out of the local minima and fall into the next
one. And so this is a very basic idea that resulted in very useful,
very interesting algorithms to minimize discrete functions. So as I
said, this is a tangent; it's not quite how we're going to discuss
this puzzle, but it was how I came up with some ideas about it.

FRV: So let me show you an example. So, there's a probability, and the
sophisticated way to think of this is that the probability will change
with the iterations. You think of temperature as something that you
have at your disposal, in the sense of annealing. So if you have a
very large temperature, then basically you take anything you like—you
just go anywhere. And if you cool off, then you become much more
greedy. If the temperature were zero, you'd be totally greedy. And you
let the temperature kind of slowly go down. So at first, you basically
move around randomly, and then you slowly cool down. This is an
example of this.

FRV: And here, the energy is measured. Let me just say that what you
want to see at the end are black and white stripes, one next to each
other, because you measure whether the guys vertically are of the same
color and the guys on the sides are the opposite color. And so, this
wonderful simulation lets you do this, and there's a cooling rate,
which is how the temperature is going to be slowly decreasing. So we
can see in this graph the global energy, this energy measure, which
should be going down. And we'll see the temperature starting at 1 and
going down to zero.

FRV: Okay, well, we didn't quite get white-black-white-black strips,
but for many purposes, that result is good enough. There's a
probability involved in the temperature. There's a cooling rate; here,
you see the cooling rate tells you how the temperature is going to
change. And here's the temperature. We start at temperature one. I
haven't explained, but it basically measures how good your
configuration is by measuring what your vertical neighbors look like
and what your horizontal neighbors look like. So if you were in
exactly the position of all white and black strips next to each other,
the energy would be zero.

FRV: So, we're in that kind of picture, with a measure where the only
solution to it is these black and white strips next to each other. I
don't know exactly, and I don't want to get too much into it, but
there's some sort of switching of the colors of the neighbors, some
particular exchange of white and black. The radius is how far around
it you are supposed to... I think it's just a swap of black and white
neighbors. I just wanted to show you the picture. I don't want to get
too much into the specifics of this example.

FRV: Let's write it again. This clearly doesn't look like
white-on-black strips, so we don't like this. And what looks like a
reasonably small number of iterations produces something that at least
you probably can live with. And you see how the energy has gone down.

Audience member: Is that...?

FRV: Yeah, I mean, the talk is not about this system. I just wanted to
use it as an excuse to bring this up and hopefully entice you to
explore it on your own. You probably can teach it, but others may not
have seen it before. I want to put the puzzle itself in a context. But
what we're going to do now is something that appeals to me, a
mathematician wanting precise answers.

FRV: In this particular instance, we have a way to understand this
minimum quite precisely, and that's really the topic of the talk. So
what I'm going to do is try to understand this maximization problem in
this puzzle by relating it to something else.

FRV: So, we started with this cycle of A's and B's. Let me cut it out
and think of a string. Let's take W to be any string, any word in A
and B. I will associate with this a certain path in the plane. This
will be a polygonal path in \(\mathbb{Z}^2\), in the lattice. There's
also some aspect that has to do with physics, which was suggested to
me by Harold, I think. What I'm going to do is describe the motion:
the A's and B's are going to be instructions for something to move in
the plane, a particle moving in the plane.

FRV: There'll be two variables. Perversely, the physicists call Q the
position, which I'll try to remember to use correctly, and P the
momentum. At any given time, there'll be two vectors that tell you
where the particle is and what the next thing it will do. There are
two ways this will move: an A and a B correspond to that. If we do an
A, we actually move one step in the direction of the momentum and keep
the momentum as it is. And a B will be to keep the position as it is
and change the momentum by -1 unit of the position.

FRV: Here's an implementation of this idea. I will start—my initial
state will start at the vector (1, 0). I think I'll use row vectors,
so it's (1, 0), and the momentum is (0, 1). So you see, the red arrow
is the position, and the blue arrow is the momentum. If I do an A, I
just move one step in the direction of the blue arrow. If I now do a
B, I change my momentum vector by minus one unit of the position. So,
it was up here and now it's pointing this way.

FRV: So, if I do A and B and I repeat this, sorry, now these vectors
are two-dimensional vectors. At every time, my moves are for A, I
change the red vector by adding one blue vector. And in this case, I
change the blue vector by subtracting one red vector. Well, they keep
moving. I start here, and they'll be whatever they are. We'll explore
and see what happens.

FRV: So let me do A and B, and I'll iterate it. Let me put it
here. Okay, so this is what happens if you iterate A and B. Let's try
ABB.

Audience member: AABB.

FRV: Well, you're never turning, right? You have to use a B. B is
changing the velocity, so if you never turn, this will just keep going
up.

Audience member: What else?

Audience member: B-A-B.

Audience member: A-A-B-B.

FRV: Oops, so it's not always the case that this thing closes
up. Okay, I'm going to come back to this. So, then, associated with a
sequence, a word in A and B, we have a path in the plane. So what we
could do to keep track of what's happening, we let the matrix \( M_k
\) be the matrix where these are the rows. We start with \( M_0 \) as
the initial state, as the identity matrix. Then, doing A is nothing
but multiplying by the matrix \( \begin{pmatrix} 1 & 1 \\ 0 & 1
\end{pmatrix} \), and doing B is multiplying by the matrix \(
\begin{pmatrix} 1 & 0 \\ -1 & 1 \end{pmatrix} \). We can call this the
state matrices, and the paths that we see are the positions.

FRV: If we look at our matrices, what we see are the first rows, which
are the positions, but we also have the second rows, which are the
momenta. They move themselves in their own copy of
\(\mathbb{Z}^2\). So let's do an example. Let me do this, so, for
example, we can get something with five vertices: do A-B-A-B-A.

So if we look at our matrices what we see are the the first rows are
the positions but we also have the second rows which are the momenta
and they move themselves and then their own copy of Z squared so let's
do an example let me do

So, for example, we can get something with 5 vertices: AB, ABB, AABB,
AABB, AB, something with 5 vertices do ABABAA

What we see is this: the dots correspond to the Q vectors, the
positions, but there's a corresponding picture for the Ps. We can read
off the Ps by looking at the tangents. Let's say we start here; the
first vector is (1, 0), and the momentum vector starts vertical,
pointing up. After B, it changes direction, and after another A and B,
it changes again. This is the path that the Ps take.

This is some path γ, and this is some dual path γ*. They both come
from projecting this path of matrices to the first row and the second
row. The key observation here is that if we look at the length of this
path, which is the number of dots, there are 5. The length of the dual
path is 7, and 7 plus 5 is 12. One of the theorems in mathematics is
that all these sums of 12 are the same for paths generated by this
method.

Another property of these paths is that they are not completely
random. How would you characterize these paths that result from
playing this A and B game? If they close, they close exactly once. The
paths contain only the origin as an internal lattice point, and this
is a key feature.

Here's an example of the paths and their duals. The theorem by Scott
states that if you have a convex polyhedron with lattice points at the
vertices and a certain number of interior lattice points, there are
finitely many possible such polytopes up to transformations.

In two dimensions, there are 16 such configurations. These are all
distinct up to SL(2,Z) transformations. For example, there's a path
with 9 points, and its dual has 3 points. These properties are crucial
for understanding the puzzle we're discussing.

Let's sketch the proof of a key result. Recall that our matrices A and
B satisfy certain properties. The paths generated by following the
game rules will lead to the same final state matrix, regardless of the
sequence used. This fact helps us bound the number of A's and B's in
the game.

The theorem is: suppose the path γ is eventually closed, meaning if
you repeat a string of A's and B's enough times, the path returns to
its initial state. For such paths, the number of A's (l_a) and the
total number of letters (L) are bounded by the inequalities 1/6 L ≤
l_a ≤ 5/6 L. This also holds symmetrically for B's.

This result limits the number of A's and B's you can have because the
path we are discussing is eventually closed. For example, AB repeated
six times (AB)^6 forms a hexagon, indicating it's eventually closed.

Thus, the pair (AB)^n, or (n/2) times, results in a path that is
eventually closed. This bound applies to such paths, limiting the
number of A's and B's you can have.

The sequence AB is eventually closed, and so the pair AB repeated \( n
\) times, or more precisely, \( n/2 \) times, forms a closed path. If
I repeat this sequence six times, it's equivalent to \( (AB)^6 \), and
this forms a closed path. The path we're discussing is eventually
closed, so this statement applies and limits the number of A's and B's
you can have because any modification by the rules of the game will
change the path itself, but it won't change the fact that it is
eventually closed because the endpoint remains the same.

Okay, so let's see how we can prove that. I'll come back to that. Let
me first prove this final state matrix idea. A word is a series of
instructions, so if you follow all of them, there's a final state.

Let me sketch the proof of this, which I like because it uses the
geometry of this path. A priori, we start with the game, which seems
like a completely discrete thing, not connected to anything else, but
with this path business, it now becomes something we can use some
elementary geometry for. So, the first observation is...

Let's say that gamma itself is closed. The idea will be more or less
the same. Let \( V_1 \) to \( V_r \) be the vertices. By "vertex," I
mean a corner; in this case, there are six, but we have also seen
squares and other shapes, so the number of vertices is not the same as
the number of B's. In fact, what is a corner? A corner in this path is
a place where instead of moving forward, we decide to change the
momentum, so it has to correspond to a B, at least one B. So, in fact,
the vertices correspond exactly to blocks of B's.

Now, let's look at a vertex. We come in from here, go out there, and
let's define the exterior angle as the angle here. One small thing to
convince yourself of is that the sum of these angles is equal to what?

Well, if we went around one time, it should be \( 2\pi \). If we went
around twice, it would be \( 2\pi \times 2 \), and so on. It's \( 2\pi
\) times the winding number.

But by this theorem that I erased, the winding number is the number of
A's plus the number of B's divided by 12, so that means that this is
\( \pi \times \text{Length}/6 \).

On the other hand, the number of these \(\theta\)'s (angles) at each
vertex is at most \(\pi\), and each block of B has to have at least a
B, so this is bounded by \( \pi \times l_b \) (number of B's).

So, we get that \( l_b/L \) (ratio of number of B's to total length)
is greater than 1/6. Now, if we do this symmetrically for the A's, we
get that it is less than 5/6. So, this gives us a bound. The key thing
is to use the geometry of this path to understand how many possible
B's there could be because the B's correspond to vertices, and
vertices are where you turn, and so there's an angle involved and a
limitation for those angles.

Anyway, I understand this was quicker than it could have been, but I
want to get to the final point. So, what I was saying before about
being eventually closed is that...

Let me use a little notation. We have a word consisting of A's and
B's, so a word in A and B. Let me define \(\rho(W)\) to be the state
matrix at the end.

So, if I were to do it in that thing, I would look at the string and
click as many times as these letters indicate, and at the end, I'll be
somewhere with some red vector, some blue vector—that's my state
matrix \( M \).

Yes, that's what I do. I look at the string, and now, as Don says,
replace the letters by the matrices and take the product of all those,
and that's \( M \). The point is that if you modify \( W \), so if \(
W' \) is a modification of \( W \) by the game's rule, then if one of
them is eventually closed, then so is the other. So, if the initial
word \( W \) consists of \( AB \) \( AB \) \( AB \), and that's
eventually closed, then the theorem applies. Because of this
statement, every other sequence that comes from having done a
modification to the original game's starting point is also eventually
closed, and therefore the theorem applies to it.

Yes, in fact, it is. Yes, indeed. That's maybe even better. Clearly,
just because the matrices themselves satisfy the rules of the
game. So, in a certain sense, if you think back to the original
question, you can take this puzzle as being a set of configurations
that you're allowed to change. You can imagine zillions of puzzles of
this kind, and this one happens to be analyzable in this form because
this replacement rule is very tied to the particular geometry of this
group.

I want to say just a couple of larger things. What is the geometric
meaning of doing the rule? Let's do the simplest case, AB itself. We
go up, then we turn, and then we go. So, an AB portion, if we started
from the beginning, would look like this. The corresponding
replacement, ABA, will look like this: we first turn, then we move,
and then we turn again. So, what happens is, in general, what you see
is that one of the paths, W, might have a piece like this, and \( W'
\) will be replaced by that.

One way to interpret this rule of the game is that in the path, you
can chop off a corner, but the corner has to be such that there is no
other lattice point involved. Let me finish with this example. Let's
do ABB, ABB, ABA, ABA. Here's an example: if we look just at the path,
there is only one corner we can chop off, which is down here. Every
other corner necessarily either goes through the middle or something's
wrong. Yes, that's all there is; there's no other corner we can chop
off without including one extra lattice point. If we look at the
string, there's only one string, ABA, that we can change to BAB, which
is right here at the bottom.

No, there should be only one. This is it. Where they can last, no,
this one cannot join to that one, no, but that's just a segment. No, I
think this is the only one, so let me do this. Let me replace ABA with
BAB and run it again, and we get the same thing with the corner
chopped off. If you look at these pictures, the greedy algorithm will
always chop corners off. What we would like to do is get this as small
as possible. What we found, well, maybe in the case of only one term,
is so few things that you don't really see it, but if you have more,
you will not be able to chop it off in the smallest possible way by
just always chopping a corner. Sometimes you have to add a corner,
which would be the inverse of this, to cut a corner somewhere else.

So, this was the puzzle I wanted to discuss, which I kind of think of
as a puzzle with a moral: greed doesn't always—should not always—you
should not cut corners, good point, but you should cut the good
corners. Greed may not always lead you to what you want. So, thank
you.
