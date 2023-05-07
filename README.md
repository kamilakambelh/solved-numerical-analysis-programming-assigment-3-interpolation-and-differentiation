Download Link: https://assignmentchef.com/product/solved-numerical-analysis-programming-assigment-3-interpolation-and-differentiation
<br>



<ol>

 <li>Interpolation code.</li>

</ol>

(a) Implement Newton’s interpolation formula.

First, implement a function construct the coefficients (divided differences) required for evaluating the Newton form of the interpolation polynomial, that is <em>f</em>[<em>x</em><sub>0</sub><em>,…,x<sub>k</sub></em>] for 0 ≤ <em>k </em>≤ <em>n</em>. This function should have the signature divdiff(x,y) and return the output [c] where

x Given sampling points. y Given function values. c The coefficients for the Newton interpolation polynomial

Now implement a function which evaluates Newton’s interpolation polynomial at a new set of points xnew. Your function should have the signature interpnewt(c,x,xnew) and return the output [ynew] where c Interpolation coefficients computed by divdiff. x The same x from divdiff, i.e, sampling points for the polynomial construction. xnew New points to evaluate the interpolating polynomial on.

ynew Values of the interpolating polynomial at xnew.

<strong>Important</strong>: The variables c,x,y,xnew and ynew, should all be numpy arrays (ndarray) with dimensions 1 × (number of points/coefficients).

<strong>Important</strong>: Also, note that the returned value from divdiff is [c] and not c itself, that is, you should put the array c inside a list (which contains the single member c) and then let divdiff output it. On the other hand, interpnewt(c,x,xnew) receives c as an input and NOT [c]. Please follow these instructions EXACTLY as they are. After you use divdiff, to use c with interpnewt(c,x,xnew) you can simply ”unpack” c from [c] by using the ’*’ operator. Here’s an example to illustrate the use of ’*’:

def example(x): return x a=[[1,2]] example(a)

Out: [[1, 2]]

example(*a)

Out: [1, 2]

Similarly, the returned value of interpnewt is [ynew] and NOT ynew.

<strong>Note</strong>: You can use Horner’s rule (google it) to make running time of the function linear in the degree of the interpolation polynomial.

<ol start="2">

 <li>Given the functions</li>

</ol>

cos5<em>x, x </em>∈ [0<em>,</em>2<em>π</em>]           <em>e<sup>x</sup>, x </em>∈ [0<em>,</em>10]<em>,          </em><em>.</em>

<ul>

 <li>For each function ESTIMATE the maximal interpolation error numerically, and plotthe error (on a <strong>logarithmic </strong>scale) as a function of the number of points <em>n </em>for equallyspaced points and Chebyshev points. Explain how you computed the estimates. Choose different values of <em>n </em>so that you get an informative graph. <strong>Add the plots to the PDF</strong>.</li>

 <li>For the first 2 functions, estimate a bound on the error with Chebyshev points fromthe graph as a function of <em>n</em>. Compare the error with the analytical bounds derived in class. Write your analysis in the PDF.</li>

</ul>

<ol start="3">

 <li>Edge Detection in images – the Sobel operator</li>

</ol>

Download the image acrop512.png from the moodle. Load the image into an numpy ndarray <em>M </em>in the same way you did with the mandril.png from assignment No. 2. Now, theoretically for each pixel in the image, we wish to calculate the central difference in the x direction and save it into a numpy ndarray <em>Dx</em>. In practice, instead of the central difference in the pixel (<em>i,j</em>) we will calculate

<em>Dx</em>(<em>i,j</em>) = 1 ∗ <em>M</em>(<em>i </em>− 1<em>,j </em>− 1) − 1 ∗ <em>M</em>(<em>i </em>− 1<em>,j </em>+ 1)+                                      (1)

2 ∗ <em>M</em>(<em>i,j </em>− 1) − 2 ∗ <em>M</em>(<em>i,j </em>+ 1)


1 ∗ <em>M</em>(<em>i </em>+ 1<em>,j </em>− 1) − 1 ∗ <em>M</em>(<em>i </em>+ 1<em>,j </em>+ 1)

Note, that this is not possible for pixels on the margins of the image ,i.e, of the form [0<em>,j</em>]<em>,</em>[511<em>,j</em>]<em>,</em>[<em>i,</em>0] and [<em>i,</em>511], so do not compute the central difference there, that is, <em>Dx</em>(<em>i,j</em>) should be of size 510×510. Do the same for the y direction and save it into a numpy ndarray

<em>Dy</em>. Now create a numpy ndarray <em>G</em>(<em>i,j</em>) = <sup>p</sup><em>Dx</em><sup>2 </sup>+ <em>Dy</em><sup>2</sup>, normalize it between 0 and 1 (by dividing all the arrays values by the maximal absolute value of the matrix), and use the imshow and imsave functions of matplotlib library to display and save it.

<ul>

 <li>Add the resulting image to your PDF.</li>

 <li>Explain why the resulting image <em>G </em>is a visualization of the original image’s gradient norm.</li>

 <li>What do we see in the image? Give a mathematical explanation to what we see.</li>

</ul>

<ol start="4">

 <li>Differentiate the functions cos<em>x</em>, <em>e<sup>x</sup></em>, and <em>x </em>at <em>x </em>= 0<em>.</em>1, 1<em>.</em>0, and 30, using single-precision forward-difference and central-difference

  <ul>

   <li>For each function and point write to the PDF the derivative and its error <em>E</em>(<em>h</em>) as a function of <em>h</em>. Use the values <em>h </em>= 10<sup>−1</sup><em>,</em>10<sup>−2</sup><em>,…,</em>10<sup>−16</sup>.</li>

   <li>Plot log<sub>10 </sub>|<em>E</em>(<em>h</em>)| versus log<sub>10 </sub><em>h</em>, and check whether the number of decimal places obtained agrees with the estimates from class. <strong>Add the plots to the PDF</strong>.</li>

   <li>See if you can identify truncation errors at large <em>h </em>and the roundoff error at small <em>h </em>in your plot. Explain how this is seen in the graph. Do the slopes agree with the predictions from class?</li>

   <li>Repeat your analysis in double precision and compare to the single precision results.</li>

  </ul></li>

</ol>