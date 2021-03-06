
# Molecular Orbital Theory

In molecular orbital theory, we build approximate electronic wavefunctions from a set of one-electron wavefunctions. These one-electron wavefunctions are called _molecular orbitals_ (MOs), and they depend on the spatial coordinates of that electron only.

$\phi _i ^ \mu = \phi_i(r^\mu) = \phi_i(x^\mu, y^\mu, z^\mu) $

where the $\mu$th electron in placed in the $i$th MO. The total $N$-electron wavefunction is built from a product of these MO's. However, from the Pauli Principle, no more than two electrons can be occupied in each MO, and two electrons in the same MO must have opposite spins. A more general statement is that of the Spin Statistics Theorem, which states that wavefunctions describing fermions (like electrons) must change sign under the exchange of two fermions. We must build in a notion of spin into our MOs, and ensure that our $N$-electron wavefunction is antisymmetric (changes sign) when two electron's positions are swapped. We introduce the _molecular spin orbital_ (MSO) (or, just **spin orbitals**)

$ \psi_i^\mu(r,s) = \phi_i(r^\mu) \omega_i(s^\mu)$ 

where the 'spin coordinate' $s$ is just some abstract, discrete, two-level quantity. You can think of it as taking on values of $+$ or $-$. It is not really used directly, but is needed to express a rigorous inner product (and thus an integral over some coordinate). In practice, the spin function takes on either spin up ($\alpha$) or spin down ($\beta$) status. Each of these spin states are orthonormal, and the integrations are expressed as 

$ \langle \alpha | \alpha \rangle =  \int \alpha^*(s) \alpha(s) ds = 1$

$\langle \beta | \beta \rangle = \int \beta^*(s) \beta(s) ds = 1 $

$\langle \beta | \alpha \rangle = \int \beta^*(s) \alpha(s) ds = 0 $

$\langle \alpha | \beta \rangle = \int \alpha^*(s) \beta(s) ds = 0 $

### Slater Determinants
By including the spin functions into our MO's, we have a sufficient incorporation of spin. To satisfy the Spin-Statistics Theorem/Pauli Principle,  the total $N$-electron wavefunction must be made to be antisymmetric (change sign) under interchange of electrons. To do this, we write the wavefunction as an **antisymmetric product** of molecular spin orbitals, otherwise known as a Slater Determinant. This construct has the advantage of automatically enforcing antisymmetry; if two electron coordinates are exchanged, we get a minus sign. 

$ \Phi = \frac{1}{\sqrt{N!}} \begin{vmatrix}
\psi_1^1 & \psi_2^1 & \psi_3^1 & ...  & \psi_N^1 \\
\psi_1^2 & \psi_2^2 & \psi_3^2 & ...  & \psi_N^2 \\
\psi_1^3 & \psi_2^3 & \psi_3^3  &...    & \psi_N^N \\
\vdots & \vdots & \vdots & \ddots &  \vdots \\
\psi_1^N & \psi_2^N & \psi_3^N  &...    & \psi_N^N \\
\end{vmatrix}$

This is not a matrix. This is a linear combination of products of one electron wavefunctions (MSO's) where the superscript denote the electron label and the subscripts denote the MSO label. Each term in the linear combination is some permutation electron labels (or, equivalently, MO labels) of the product $\psi_1^1 \psi_2^2 \dots \psi_N^N$. Odd permutations give a minus sign, and even permutations are positive. This can be expressed in another way, using the **antisymmetrizer** operator $\hat{A}$:

$ \Phi = \sqrt{N!} \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) $

where $ \hat{A} = \frac{1}{N!} \sum_{P \in S_N} (-1)^{\pi} \hat{P} $ which is summing over all permutation operators which exist for an ordered sequenced of $N$ objects, odd permutations negative, even permutations positive. Colloquially, the antisymmetrizer says "Hey, you see that product of MO's? I'm going to sum all possible permutations of them. If a permutation needs an odd number of tranpositions to get back to the original, its an odd permutation, and that term in the linear combination gets a minus sign. If its an even permutation, its remains positive." A simple example of a two electron wavefunction with two MO's is

$\Phi = \sqrt{2!} \hat{A} (\psi_1^1 \psi_2^2) = \sqrt{2!}( \psi_1^1 \psi_2^2 - \psi_1^2 \psi_2^1)$ 

Note how we exchanged the _electron labels_ (superscripts) in the second term. It may seem odd at first, but it is equivalent to exchange electron labels vs MO labels. This is useful to note for later derivations. In the context of the above example, we could exchange the _MO labels_ (subscripts), and it gives the same result

$\sqrt{2!}( \psi_1^1 \psi_2^2 - \psi_2^1 \psi_1^2)$ 

where that second term is just flipped around compared to before (the product of the two MO's commute, as you might expect). 

## Orthonormality of orbitals

Suppose we collect our set of spin orbitals, which make up our Slater Determinant wavefunction, into a row vector:

$ \boldsymbol{\psi} = [\psi_1, \psi_2, \dots, \psi_N] $

and subject this row vector to a linear transformation, by multiplying it by some NxN nonsingular matrix

$\psi_k' = \sum_\lambda \psi_\lambda A_{\lambda k} $

$\boldsymbol{\psi'} = \boldsymbol{\psi} \boldsymbol{A}$ 

Note we can build a Slater determinant made up of spin orbitals in $\boldsymbol{\psi'}$, or a Slater determinant made up of spin orbitals in $\boldsymbol{\psi}$. 

The corresponding expression for relating the two Slater determinants is 

$ \Phi' = \Phi \mathrm{Det}(\boldsymbol{A}) $

this means our wavefunction is only altered by a scalar quantity under linear transformations. This does not change anything about the wavefunction or quantities obtained from it, such as the energy (to see this, imagine scaling the wavefunction in the time independent Schrodinger equation by a constant). 

Why am I talking about this? Well, this all means that we can always multiply our orbitals by a matrix $\boldsymbol{A}$. **This implies we can always choose $\boldsymbol{A}$ such that our spin orbitals are orthonormal**

$ \int \psi^*_i \psi_j d\tau = \delta_{ij} $

One such way to ensure any linearly independent set of spin orbitals are orthonormal is using the Gram Schmidt orthogonalization procedure. We will be doing something else, as we will discuss later. The important takeaway is **we will always assume our spin orbitals are orthonormal from here on**. If we didn't, our equations would not be easy to deal with.

A final important note is that **since our spin orbitals are orthonormal, the corresponding Slater determinant is normalized**:

\\[ \int \Phi^* \Phi d\tau = 1 \\]

## The Hamiltonian, the Schrodinger Equation, and the First Slater-Condon Rule

Recall our previously discussed clamped-nuclei (Born-Oppenheimer) electronic Hamiltonian, expressed in atomic units as,

\\[ \hat{H} = -\sum_\limits{i} \frac{1}{2} \nabla^2_{\boldsymbol{r}_i} - \sum_\limits{i} \sum_\limits{A} \frac{Z_A}{|\boldsymbol{R}_A - \boldsymbol{r}_i|} + \sum_\limits{i < j} \frac{1}{\boldsymbol{r}_{ij}} + V_{\mathrm{nuc}} \\]

where the sum over $i < j $ is just a sum over all pairs of $i,j$ up to N that obey that inequality $(1,2), (1,3), .. (N-1,N)$. From here on, we are going to drop the nuclear repulsion energy term $V_{\mathrm{nuc}}$ since it just a constant factor we will add to the electronic energy later. 
It will be much more convenient to express it as a sum of one electron and two-electron operators

\\[ \hat{H} = \sum_\limits{i} \hat{h}(i) + \sum_\limits{i < j} \hat{g}(i,j)  \\]


where we express them suggestively as functions of the electronic coordinates of electron $i$ and $j$. Note the sum over nuclei $A$ is gone; since the nuclei are fixed, we can just remove the sum, and understand that the nuclear-electron attraction requires a sum over all nuclei. 

### Applying the Schrodinger Equation

We have thus far defined a **Hamiltonian** which describes all of the relevent energetic interactions in our system. We have also defined an approximate form for an  **$N$-electron wavefunction, the Slater determinant**, which is an antisymmetric linear combination of **products of one-electron wavefunctions, which we called spin orbitals.** The time independent Schrodinger equation says

\\[ \hat{H} |\Psi \rangle = E |\Psi \rangle \\]

so, we should be able to write down what the electronic energy is for our single Slater determinant wavefunction. Using a Slater determinant $\Phi$ as the wavefunction, we can multiply each side by the bra $\langle \Phi | $ and obtain

\\[\langle \Phi |  \hat{H} |\Phi \rangle = E\langle \Phi |\Phi \rangle \\]

assuming an **orthonormal** set of spin orbitals, the Slater determinant is normalized so we just have

\\[\langle \Phi |  \hat{H} |\Phi \rangle = E \\]

Let's not be confused by the abstraction here. This is an _integral_ with a bunch of operators and functions sandwiched inside. We might write it in an overwhelmingly explicit way by using our definitions of each thing,

\\[E = \int \sqrt{N!} \hat{A} (\psi_1^{1*} \psi_2^{2*} \dots \psi_N^{N*})  \left[ -\sum_\limits{i} \frac{1}{2} \nabla^2_{\boldsymbol{r}_i} - \sum_\limits{i} \sum_\limits{A} \frac{Z_A}{|\boldsymbol{R}_A - \boldsymbol{r}_i|} + \sum_\limits{i < j} \frac{1}{\boldsymbol{r}_{ij}} \right] \sqrt{N!} \hat{A} (\psi_1^{1} \psi_2^{2} \dots \psi_N^{N}) d\tau_1 \dots d\tau_N \\]

Yikes. See why we don't do that? We didn't even expand our spin orbitals into their explicit form $\psi_1^1(\boldsymbol{r}_1,s_1) = \phi_1(\boldsymbol{r}_1) \omega_1(s_1)$. Note we use $\tau$ for the integration over both spin and spatial coordinates. Let's clean the above up a little:

\\[E = \int \sqrt{N!} \hat{A} (\psi_1^{1*} \psi_2^{2*} \dots \psi_N^{N*})  \left[ \sum_\limits{i} \hat{h}(i) + \sum_\limits{i < j} \hat{g}(i,j) \right] \sqrt{N!} \hat{A} (\psi_1^{1} \psi_2^{2} \dots \psi_N^{N}) d\tau_1 \dots d\tau_N \\]

Noting the following facts:

1. An integral $\int A + B$ is really just $\int A + \int B$ 
2. An integral $\int f(r_1) g(r_2) dr_1 dr_2 =\int f(r_1) dr_1 \cdot \int g(r_2)  dr_2   $
3. The antisymmetrizer $\hat{A}$ produces a linear combination of products of spin orbitals
4. The operators which sum over different electrons can be expanded and separated into separate integrals according to the above rules

the above energy expression is really just an enormously complex linear combination of products of simple integrals over spin orbitals and operators. This will become apparent in our derivation of the energy expression, where the above integral monstrosity simplifies tremendously to the following, which is commonly denoted as the _first Slater-Condon Rule_, 

\\[ E =  \sum_\limits{i} \langle\psi_i|h(i)|\psi_i \rangle + \sum_\limits{i<j}  \langle \psi_j\psi_i|g(i,j)|\psi_i\psi_j \rangle - \langle \psi_i\psi_j|g(i,j)|\psi_j\psi_i \rangle \\]

This gives a general expression for the electronic energy, assuming a Slater determinant wavefunction made up of orthonormal spin orbitals and the above defined electronic Hamiltonian. 
## Derivation of First Slater-Condon Rule
Back to bra-ket notation, we begin with 
\\[E = \langle \Phi  | \sum_\limits{i} \hat{h}(i) + \sum_\limits{i < j} \hat{g}(i,j) | \Phi \rangle\\]


We can separate out just the one electron part and two electron parts of our energy expression to make things a little easier. 

### One-electron energy 
Using our definition of Slater determinant,
\\[ \langle \Phi | \sum_\limits{i} \hat{h}_i | \Phi \rangle = N! \langle \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) |  \sum_\limits{i} \hat{h}(i)  | \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) \rangle \\]

To simplify this, we note three facts:
1. $\hat{A}$ is a Hermitian operator. Like all Hermitian operators, we can move it through bra's and ket's $ \langle f | \hat{A}| g \rangle = \langle \hat{A} f | g \rangle = \langle f | \hat{A} g \rangle $

\\[ = N! \langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{A}  \sum_\limits{i} \hat{h}(i)  | \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) \rangle \\]

2. $\hat{A}$ commutes with $\hat{H}$, and therefore $\hat{h}$
\\[ = N! \langle \psi_1^1 \psi_2^2 \dots \psi_N^N |  \sum_\limits{i} \hat{h}(i)  | \hat{A}  \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) \rangle \\]

3. $\hat{A}$ is _idempotent_ ;  $\hat{A}^2 = \hat{A}$, so we are left with just one $\hat{A}$.

\\[ = N! \langle \psi_1^1 \psi_2^2 \dots \psi_N^N |  \sum_\limits{i} \hat{h}(i)  | \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) \rangle \\]











so far so good. Now lets flip-flop $\hat{A}$ and the one electron operator, ( note we can only do this because these operators are Hermitian and they commute) and expand the sum over $\hat{h}$ explicitly and see if that leads anywhere.

\\[ = N! \langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{A} |  \hat{h}(1)\psi_1^1 \psi_2^2 \dots \psi_N^N + \psi_1^1 \hat{h}(2) \psi_2^2 \dots \psi_N^N  + \dots + \psi_1^1  \psi_2^2 \dots \hat{h}(N) \psi_N^N \rangle \\]

Alright, so now in the ket we just have a sum of spin orbital products, where the one electron operator for the $i$th electron is being applied to the spin orbital which holds that electron. It has no effect on any of the other spin orbitals. The above equation looks ugly, but it simplifies tremendously. See that first term in the ket? The "$ \hat{h}(1)\psi_1^1 \psi_2^2 \dots \psi_N^N  $" ? We are going to investigate just that term alone, and deduce what analogously will occur for all _other_ terms in the ket. So, we just have this:
\\[ \langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{A} |  \hat{h}(1)\psi_1^1 \psi_2^2 \dots \psi_N^N \rangle \\]

Now, recall the antisymmetrizer $\hat{A}$ is going to take what's in that ket and expand it as an antisymmetric sum of spin orbital products, each a different permutation with the appropriate parity (sign). It turns out, we can antisymmetrize over the spin orbital indices (subscripts) **OR** the electron label indices (superscripts), and we get the same thing. We discussed this earlier, and you will convince yourself of this in a homework problem.

Let's write out a few terms that occur when applying the antisymmetrizer. I'm going to be permuting the spin orbital indices, because I like that it keeps the electrons ordered from left to right in every product of spin orbitals. 

$\langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{h}(1) |\psi_1^1 \psi_2^2 \dots \psi_N^N  \rangle - \langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{h}(1) |\psi_2^1 \psi_1^2 \dots \psi_N^N  \rangle  + $(all permutations of spin orbitals in ket with appropriate sign)

Remember each of  these terms are **integrals** over **orthonormal spin orbitals**. Thus they are multiplicatively separable for functions over different integration coordinates. The first term above (ignoring spin function coordinates for now, they don't end up doing anything here) looks like a product of integrals,

\\[\int \psi_1^{*}(\boldsymbol{r}_1) \hat{h}(\boldsymbol{r}_1) \psi_1(\boldsymbol{r}_1) d\boldsymbol{r}_1 \int \psi_2^{*}(\boldsymbol{r}_2)\psi_2(\boldsymbol{r}_2) d\boldsymbol{r}_2 \cdots \int \psi_N^*(\boldsymbol{r}_N)\psi_N(\boldsymbol{r}_N) d\boldsymbol{r}_N \\]

But, our spin orbitals are orthonormal, so most of these just equal 1. We are left with just the first integral
\\[ \langle \psi_1^1 | \hat{h}(1) | \psi_1^1 \rangle \\]
Hol' up tho. There's a bunch of other terms in our antisymmetrizer expansion above. Let's take a close look at that second term, in its integral form,

\\[\int \psi_1^{*}(\boldsymbol{r}_1) \hat{h}(\boldsymbol{r}_1) \psi_2(\boldsymbol{r}_1) d\boldsymbol{r}_1 \int \psi_2^{*}(\boldsymbol{r}_2)\psi_1(\boldsymbol{r}_2) d\boldsymbol{r}_2 \cdots \int \psi_N^*(\boldsymbol{r}_N)\psi_N(\boldsymbol{r}_N) d\boldsymbol{r}_N \\]

**The first two integrals are 0** by orthonormality because the spin orbitals are different. 

It's not hard to convince yourself that _every_ permutation of the ket spin orbital product is going to become 0 due to spin-orbital orthonormality. So, we are only left with one term from the antisymmetrizer expansion.

\\[ \langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{A} |  \hat{h}(1)\psi_1^1 \psi_2^2 \dots \psi_N^N \rangle = \langle \psi_1^1 | \hat{h}(1) | \psi_1^1 \rangle \\]

 This is going to be true for _every_ one electron operator $\hat{h}(i)$ in the summation in the ket from earlier: 

 \\[ \langle \Phi | \sum_\limits{i} \hat{h}_i | \Phi \rangle  = N! \langle \psi_1^1 \psi_2^2 \dots \psi_N^N | \hat{A} |  \hat{h}(1)\psi_1^1 \psi_2^2 \dots \psi_N^N + \psi_1^1 \hat{h}(2) \psi_2^2 \dots \psi_N^N  + \dots + \psi_1^1  \psi_2^2 \dots \hat{h}(N) \psi_N^N \rangle \\]

 We can conclude then, after factoring out the $\frac{1}{N!}$ factor built into $\hat{A}$ and canceling the $N!$ factor
 \\[ \langle \Phi | \sum_\limits{i} \hat{h}(i) | \Phi \rangle  = \sum_\limits{i} \langle \psi_i | \hat{h}(i) | \psi_i \rangle \\]

 This corresponds to the 'one electron energy'.

 

### Two-electron energy

 Our Hamiltonian has another operator; the two-electron operator $\hat{g}$

 \\[E = \langle \Phi  | \sum_\limits{i} \hat{h}(i) + \sum_\limits{i < j} \hat{g}(i,j) | \Phi \rangle\\]

We need to find the energy contribution of this operator as well.
 \\[ \langle \Phi | \sum_\limits{i < j} \hat{g}(i,j) | \Phi \rangle = N! \langle \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N) |  \sum_\limits{i < j} \hat{g}(i,j) | \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N)  \rangle  \\]

 We use the same facts as before ($\hat{A}$ is Hermitian, idempotent, and commutes with $\hat{g}$) to simplify:
\\[  = N! \langle \psi_1^1 \psi_2^2 \dots \psi_N^N |  \sum_\limits{i < j} \hat{g}(i,j) | \hat{A} (\psi_1^1 \psi_2^2 \dots \psi_N^N)  \rangle  \\]

Swapping $\hat{A}$ and $\hat{g}$ and expanding the sum over $i < j$ in the ket we obtain

$= N! \langle \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N | \hat{A} |  \hat{g}(1,2) \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N + \hat{g}(1,3) \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N + \dots + \hat{g}(N-1,N) \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N  \rangle $

As before, let's look at just one term in the expansion, the one containing $\hat{g}(1,2)$:

$ \langle \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N | \hat{A} |  \hat{g}(1,2) \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N  \rangle $

The antisymmetrizer operator $\hat{A}$ expands the ket as a sum over all permutations of the spin orbital product. Let's write down the first few terms, permuting the spin orbital labels (subscripts):

$ \langle \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N |\hat{g}(1,2)| \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N  \rangle  -  \langle \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N |\hat{g}(1,2)| \psi_2^1 \psi_1^2 \psi_3^3 \dots \psi_N^N  \rangle  + \langle \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N |\hat{g}(1,2)| \psi_3^1 \psi_1^2 \psi_2^3 \dots \psi_N^N  \rangle + ...  $

The first term can be rearranged into a product of integrals which only depend on like-integration variables 

$ \langle \psi_1^1 \psi_2^2 | \hat{g}(1,2) | \psi_1^1 \psi_2^2 \rangle \langle \psi_3^3 | \psi_3^3 \rangle ... \langle \psi_N^N | \psi_N^N \rangle = \langle \psi_1^1 \psi_2^2 | \hat{g}(1,2) | \psi_1^1 \psi_2^2 \rangle  $

Notice how the superscripts, which denote electron coordinate labels, are always kept together in the same integral (bra-ket).

The second term is also nonzero:

$ -\langle \psi_1^1 \psi_2^2 | \hat{g}(1,2) | \psi_2^1 \psi_1^2 \rangle \langle \psi_3^3 | \psi_3^3 \rangle ... \langle \psi_N^N | \psi_N^N \rangle = -\langle \psi_1^1 \psi_2^2 | \hat{g}(1,2) | \psi_2^1 \psi_1^2 \rangle $

The third term, and all other terms arising from various permutations of the ket, do not survive. Let's look at an example to see why. The third term from above is

$\langle \psi_1^1 \psi_2^2 \psi_3^3 \dots \psi_N^N |\hat{g}(1,2)| \psi_3^1 \psi_1^2 \psi_2^3 \dots \psi_N^N  \rangle $

Now, the spin orbitals which involve coordinates of electrons 1 and 2 are stuck with the operator $\hat{g}(1,2)$ in the same integral. Thus, ignoring spin functions, we have the following

$\int \psi_1(\boldsymbol{r}_1) \psi_2(\boldsymbol{r}_2) \hat{g}(1,2) \psi_3(\boldsymbol{r}_1) \psi_1(\boldsymbol{r}_2) d\boldsymbol{r}_1d\boldsymbol{r}_2  \langle \psi_3^3 | \psi_2^3 \rangle \langle \psi_4^4 | \psi_4^4 \rangle \dots \langle \psi_N^N | \psi_N^N \rangle$

The second integral in this product $\langle \psi_3^3 | \psi_2^3 \rangle$ is zero by orthonormality of the spin orbitals. So this whole term goes to zero. Every other term (fourth, fifth, ... N!th) resulting from expanding the antisymmetrizer also will go to zero. Generally, for a given operator $\hat{g}(i,j)$ , a 0-overlap integral (like $\langle \psi_3^3 | \psi_2^3 \rangle$ above)  will **always** factor out and cancel terms whose two electron integral part includes any spin orbitals other than $\psi_i$ and $\psi_j$. To put it another way, the only two terms which survive are those whose two electron integral part, containing the operator $\hat{g}(i,j)$, contains either $\psi_i^i\psi_j^j$ or $\psi_j^i\psi_i^j$ in the ket.

The above reasoning is not only true for $\hat{g}(1,2)$, but for all $\hat{g}(i,j)$, so in our original expansion, 

$\langle \Phi | \sum_\limits{i < j} \hat{g}(i,j) | \Phi \rangle  = N! \langle \psi_1^1 \psi_2^2  \dots \psi_N^N | \hat{A} |  \hat{g}(1,2) \psi_1^1 \psi_2^2  \dots \psi_N^N + \hat{g}(1,3) \psi_1^1 \psi_2^2  \dots \psi_N^N + \dots + \hat{g}(N-1,N) \psi_1^1 \psi_2^2  \dots \psi_N^N  \rangle $

each $i,j$ pair with $i < j$ will pick up exactly two terms

\\[ \langle \psi_i^i \psi_j^j | \hat{g}(i,j)| \psi_i^i \psi_j^j \rangle - \langle \psi_i^i \psi_j^j | \hat{g}(i,j)| \psi_j^i \psi_i^j \rangle \\]

leading us to write the total energy contribution of the two electron operator as a sum over $i < j$,
\\[\langle \Phi | \sum_\limits{i < j} \hat{g}(i,j) | \Phi \rangle = \sum_\limits{i < j}  \langle \psi_i^i \psi_j^j | \hat{g}(i,j)| \psi_i^i \psi_j^j \rangle - \langle \psi_i^i \psi_j^j | \hat{g}(i,j)| \psi_j^i \psi_i^j \rangle \\]

We have shown that the expectation value of our electronic Hamiltonian for a Slater determinant wavefunction composed of orthonormal spin orbitals simplifies to the following relation

\\[ E = \sum_\limits{i} \langle\psi_i|h(i)|\psi_i \rangle + \sum_\limits{i<j}  \langle \psi_j\psi_i|g(i,j)|\psi_i\psi_j \rangle - \langle \psi_i\psi_j|g(i,j)|\psi_j\psi_i \rangle \\]





# Summary and Commentary
Hopefully you can see that we have done nothing weird (ad hoc, arbitrary assertions) to get to this result. We were able to come up with our electronic Hamiltonian by logically thinking about all the physical interactions in our system. This Hamiltonian isn't exact; we are neglecting all relativistic effects, as well as nuclear motion (Born-Oppenheimer approximation). Nevertheless, this Hamiltonian is _really really good_. We further reasoned our wavefunction for a many electron system would be best approximated by a product of one electron wavefunctions, called spin orbitals. There's a few reasons for this. First, assuming electrons occupy local spatial functions in a molecule is not a bad approximation; we know they do from the exact solution of the Hydrogen atom. The only thing that should cause us to hesitate is that electrons can in principle move around and go to different orbitals, especially when influenced by each other's repulsion. We are mostly ignoring this, except the exchange term in our energy provides a little bit of what we need (_electron correlation_) for that. Correlated methods such as coupled cluster attempt to patch out this issue. We finally note that we are not too worried about coming up with one electron wavefunctions; we have a decent idea of what they should look like from the Hydrogen atom solutions.

But, a product of one electron wavefunctions is not good enough in itself. We need an _antisymmetric product_, a Slater determinant, to account for the fundamental truth that fermionic wavefunctions must change sign when electrons are exchanged. 

So, we have a Hamiltonian and a form for a wavefunction. We don't assume anything about the details of the wavefunction, other than that it is normalized, and each spin orbital is orthonormal (they can _always_ be made to be orthonormal). This is sufficient to plug things into the time-independent Schrodinger equation and get an expression for the energy. 

So, are we done? Have we just solved Quantum Chemistry? We have an equation for the energy of any molecular system, after all. Well... no. Sure, we can get _some energy_ by just choosing some random functions for our orbitals. This probably won't work out too well. We need a systematic way to get a good energy from this expression. This is what Hartree-Fock theory does for us.


The Hartree Fock equations are obtained by minimizing the energy of the first Slater-Condon rule under the constraint the orbitals are orthonormal. This makes sense, since we depended on orbital orthonormality over and over again in order to derive the energy expression. The only way we can alter the result of our energy is by changing our spin orbitals. By minimizing the energy through orbital variations, we are implicitly believing in the Variational Principle; any trial wavefunction we write down which depends on a set of parameters (the functional form of our spin orbitals) will be bounded below by the true ground state energy. So, varying our wavefunction's parameters such that the energy is lowest will give the best Slater determinant wavefunction and best energy. The Hartree-Fock equations provide a method for finding this best single Slater determinant wavefunction and energy. We will discuss this more later.




# Exercises 

1. Show that for an orthonormal set of spin orbitals, the Slater determinant composed of them is normalized,

\\[ \langle \Phi | \Phi \rangle = \int \Phi^* \Phi d\tau = 1 \\]

Hint: use the definition of a Slater determinant combined with tricks used in our derivation of the first Slater-Condon rule

2. Suppose you have a system with 3 electrons in 3 molecular spin orbitals $(\psi_1^1 \psi_2^2 \psi_3^3)$. "Antisymmetrize" this product wavefunction by forming a Slater determinant using the definition of a Slater Determinant. Explicitly expand each term in two ways:  
  i. Permuting the electron labels  
  ii. Permuting the MO labels  
Show these two expansions our equivalent by labeling equivalent terms. 

3. Derive the first Slater-Condon rule for the value of the energy for a Slater determinant wavefunction, beginning from the time-independent Schrodinger equation and the following simplified electronic Hamiltonian:

\\[ \hat{H} = \sum_\limits{i} \hat{h}(i) + \sum_\limits{i < j} \hat{g}(i,j) \\]

4. Explain in your own words how one gets from the time-indepedent Schrodinger equation to the Hartree-Fock equations (NOT the Roothaan-Hall or Pople-Nesbet equations). Include a brief description of each of the following:  
 i. the Hamiltonian  
 ii. the nature of the wavefunction and its components  
 iii.  how the best electronic energy is obtained for this wavefunction
 iv. how the Hartree-Fock equations relate to this wavefunction


5. Suppose you perform a linear transformation $\boldsymbol{A}$ of $N$ molecular spin orbitals describing an $N$-electron system, collected in a vector $\boldsymbol{\psi} = [\psi_1, \psi_2, ..., \psi_N]$ to form a new set of spin orbitals $\boldsymbol{\psi'}$:  
\\[\boldsymbol{\psi'} = \boldsymbol{\psi} \boldsymbol{A}  \\]
  show that for the corresponding Slater determinants built from these spin orbital sets that the following is true:
\\[ \Phi' = \Phi \det(\boldsymbol{A})\\]
