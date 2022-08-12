---
title: transform-function
slug: Web/CSS/transform-function
translation_of: Web/CSS/transform-function
---
<p>{{ CSSRef("CSS Transforms") }}The <code>&lt;transform-function&gt;</code> CSS data type denotes a function applied to an element's representation in order to modify it. Usually such transform may be expressed by matrices and the resulting images can be determined using matrix multiplication on each point.</p>

<h2 id="Coordinates_for_2D_graphics">Coordinates for 2D graphics</h2>

<p>There are several coordinate models used when describing transformation. The most common are the Cartesian coordinate system and homogeneous coordinates.</p>

<h3 id="笛卡兒坐標系">笛卡兒坐標系</h3>

<p><a href="/@api/deki/files/5796/=coord_in_R2.png"><img src="/files/3438/coord_in_R2.png" style="float: right; width: 171px;"></a></p>

<p>In <a href="http://en.wikipedia.org/wiki/Cartesian_coordinate_system">Cartesian coordinates</a> each point of the <a href="http://en.wikipedia.org/wiki/Euclidean_geometry">Euclidian space</a> is described using two values, the abscissa and the ordinate. The origin, the <code>(0, 0)</code> is the top-left corner of the element. Unlike the usual geometric convention, and like most cases in computer graphics, the y-axis goes to the bottom. Each point is mathematically described using the vector notation <code>(x,y)</code>.</p>

<p>Each linear function is described using a 2x2 matrix like:</p>

<div style="text-align: center;">
<p><math> <mfenced> <mtable> <mtr><mtd>a</mtd><mtd>c</mtd></mtr> <mtr><mtd>b</mtd><mtd>d</mtd></mtr> </mtable> </mfenced> </math></p>
</div>

<p>Applying the transformation consists in doing, for each point, the matrix multiplication between both:</p>

<div style="text-align: center;"><a href="/@api/deki/files/5799/=transform_functions_generic_transformation_cart.png"><img src="/@api/deki/files/5799/=transform_functions_generic_transformation_cart.png?size=webview" style="height: 32px; width: 189px;"></a>.</div>

<p>It is possible to apply several transformations in a row:</p>

<div style="text-align: center;"><a href="/@api/deki/files/5800/=transform_functions_transform_composition_cart.png"><img src="/@api/deki/files/5800/=transform_functions_transform_composition_cart.png?size=webview" style="height: 32px; width: 313px;"></a>.</div>

<p>With this notation, it is possible to describe, and therefore composite, most usual transformations: rotations, scaling, or skewing. In fact all transformations that are linear functions can be described. One major transformation is not linear and therefore must be special-cased when using this notation: translation. The translation vector (tx, ty) must be expressed separately, as two more parameters.</p>

<p><a href="http://en.wikipedia.org/wiki/August_Ferdinand_M%C3%B6bius">Möbius</a>' <a href="http://en.wikipedia.org/wiki/Homogeneous_coordinates">homogeneous coordinates</a> in <a href="http://en.wikipedia.org/wiki/Projective_geometry">projective geometry</a> leading to 3x3 transformation matrices, though more complex and unusual for non-specialists, doesn't suffer from the translation limitation as these can be expressed as linear functions in this algebra, removing the need for special cases.</p>

<h2 id="Coordinates_for_3D_graphics">Coordinates for 3D graphics</h2>

<h2 id="Functions_defining_transformations">Functions defining transformations</h2>

<h3 id="matrix()"><code>matrix()</code></h3>

<p>The <code>matrix()</code> CSS function specifies a homogeneous 2D transformation matrix comprised of the specified six values. The constant values of such matrices are implied and not passed as parameters; the other parameters are described in the column-major order.</p>

<p><code>matrix(a, b, c, d, tx, ty)</code> is a shorthand for <code>matrix3d(a, b, 0, 0, c, d, 0, 0, 0, 0, 1, 0, tx, ty, 0, 1)</code>.</p>

<div class="note"><strong>Note:</strong> Until Firefox 16, Gecko accepted a {{cssxref("&lt;length&gt;")}} value for <strong>tx</strong> and <strong>ty</strong>.</div>

<h4 id="表達式">表達式</h4>

<pre class="syntaxbox">matrix(<em>a</em>, <em>b</em>, <em>c</em>, <em>d</em>, <em>tx</em>, <em>ty</em>)
</pre>

<h4 id="值">值</h4>

<dl>
 <dt><em>a</em> <em>b</em> <em>c</em> <em>d</em></dt>
 <dd>Are {{cssxref("&lt;number&gt;")}} describing the linear transformation.</dd>
 <dt><em>tx</em> <em>ty</em></dt>
 <dd>Are {{cssxref("&lt;number&gt;")}} describing the translation to apply.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced> <mtable> <mtr><mtd>a</mtd><mtd>c</mtd></mtr> <mtr><mtd>b</mtd><mtd>d</mtd></mtr> </mtable> </mfenced> </math></td>
   <td><math> <mfenced> <mtable> <mtr><mtd>a</mtd><mtd>c</mtd><mtd>ty</mtd></mtr><mtr><mtd>b</mtd><mtd>d</mtd><mtd>tx</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced> <mtable> <mtr><mtd>a</mtd><mtd>c</mtd><mtd>ty</mtd></mtr><mtr><mtd>b</mtd><mtd>d</mtd><mtd>tx</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced> <mtable> <mtr><mtd>a</mtd><mtd>c</mtd><mtd>0</mtd><mtd>tx</mtd></mtr><mtr><mtd>b</mtd><mtd>d</mtd><mtd>0</mtd><mtd>ty</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[a b c d tx ty]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="matrix3d()"><code>matrix3d()</code></h3>

<p>The <code>matrix3d()</code> CSS function describes a 3D transform as a 4x4 homogeneous matrix. The 16 parameters are described in the column-major order.</p>

<div class="note"><strong>Note:</strong> Until Firefox 16, Gecko accepted a {{cssxref("&lt;length&gt;")}} value for <strong>a4</strong>, <strong>b4</strong> and <strong>c4</strong>.</div>

<h4 id="表達式_2">表達式</h4>

<pre class="syntaxbox">matrix3d(a1, b1, c1, d1, a2, b2, c2, d2, a3, b3, c3, d3, a4, b4, c4, d4)</pre>

<h4 id="值_2">值</h4>

<dl>
 <dt><em>a1 b1 c1 d1</em> <em>a2 b2 c2 d2 </em><em>a3 b3 c3 d3</em> <em>d4</em></dt>
 <dd>Are {{cssxref("&lt;number&gt;")}} describing the linear transformation.</dd>
 <dt><em>a4</em> <em>b4 c4</em></dt>
 <dd>Are {{cssxref("&lt;number&gt;")}} describing the translation to apply.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">This transform applies to the 3D space and cannot be represented on the plan.</td>
   <td colspan="1" rowspan="2">Cartesian-coordinate matrix doesn't allow to represent a generic 3d affine transforms as translations are not linear transforms.</td>
   <td colspan="1" rowspan="2"><math><mfenced><mtable><mtr><mtd>a1</mtd><mtd>a2</mtd><mtd>a3</mtd><mtd>a4</mtd></mtr><mtr><mtd>b1</mtd><mtd>b2</mtd><mtd>b3</mtd><mtd>b4</mtd></mtr><mtr><mtd>c1</mtd><mtd>c2</mtd><mtd>c3</mtd><mtd>c4</mtd></mtr><mtr><mtd>d1</mtd><mtd>d2</mtd><mtd>d3</mtd><mtd>d4</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="perspective()"><code>perspective()</code></h3>

<p>The <code>perspective()</code> CSS function defines the distance between the z=0 plane and the user in order to give to the 3D-positioned element some perspective. Each 3D element with z&gt;0 becomes larger; each 3D-element with z&lt;0 becomes smaller. The strength of the effect is determined by the value of this property.</p>

<h4 id="表達式_3">表達式</h4>

<pre class="syntaxbox">perspective(l)
</pre>

<h4 id="值_3">值</h4>

<dl>
 <dt><em>l</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} giving the distance from the user to the z=0 plane. It is used to apply a perspective transform to the element. If it is 0 or a negative value, no perspective transform is applied.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">
    <p>This transform applies to the 3D space and cannot be represented on the plan.</p>
   </td>
   <td colspan="1" rowspan="2">A perspective is not a linear transform in ℝ<sup>3</sup> and cannot be represented using a matrix in the Cartesian coordinates system.</td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd><mo>−</mo>1<mo>/</mo>d</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="rotate()"><code>rotate()</code></h3>

<p><img src="/@api/deki/files/5976/=transform-functions-rotate_19.5.png" style="float: left;">The <code>rotate()</code> CSS function defines a transformation that moves the element around a fixed point (as specified by the {{ Cssxref("transform-origin") }} property) without deforming it. The amount of movement is defined by the specified angle; if positive, the movement will be clockwise, if negative, it will be counter-clockwise. A rotation by 180° is called <em>point reflection</em>.</p>

<h4 id="表達式_4">表達式</h4>

<pre class="syntaxbox">rotate(<em>a</em>)
</pre>

<h4 id="值_4">值</h4>

<dl>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle of the rotation. A positive angle denotes a clockwise rotation, a negative angle a counter-clockwise one.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced> <mtable> <mtr><mtd>cos(a)</mtd><mtd>-sin(a)</mtd></mtr> <mtr><mtd>sin(a)</mtd><mtd>cos(a)</mtd></mtr></mtable></mfenced></math></td>
   <td><math> <mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>-sin(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>sin(a)</mtd><mtd>cos(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>-sin(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>sin(a)</mtd><mtd>cos(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>-sin(a)</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>sin(a)</mtd><mtd>cos(a)</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[cos(a) </code>sin(<em>a</em>)<code> -sin(a) cos(<em>a</em>) 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="rotate3d()"><code>rotate3d()</code></h3>

<p>The <code>rotate3d()</code>CSS function defines a transformation that moves the element around a fixed axis without deforming it. The amount of movement is defined by the specified angle; if positive, the movement will be clockwise, if negative, it will be counter-clockwise.</p>

<p>In the 3D space, rotations have three degrees of liberty, describing an axis of rotation. The axis of rotation is defined by an [x, y, z] vector and pass by the origin (as defined by the {{ cssxref("transform-origin") }} CSS property. If the vector is not <em>normalized</em>, that is the sum of the square of its three coordinates is not 1, it will be normalized internally. A non-normalizable vector, like the null vector, [0, 0, 0], will cause the rotation not to be applied, without invaliding the whole CSS property.</p>

<div class="note">In opposition to rotations in the plane, the composition of 3D rotations is usually not commutative; it means that the order in which the rotations are applied is crucial.</div>

<h4 id="表達式_5">表達式</h4>

<pre class="syntaxbox">rotate3d(<em>x</em>, <em>y</em>, <em>z</em>, <em>a</em>)
</pre>

<h4 id="值_5">值</h4>

<dl>
 <dt><em>x</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} describing the x-coordinate of the vector denoting the axis of rotation.</dd>
 <dt><em>y</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} describing the y-coordinate of the vector denoting the axis of rotation.</dd>
 <dt><em>z</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} describing the z-coordinate of the vector denoting the axis of rotation.</dd>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle of the rotation. A positive angle denotes a clockwise rotation, a negative angle a counter-clockwise one.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1"><a href="/@api/deki/files/5987/=transform-functions-rotate3d_cart.png"><img src="/@api/deki/files/5987/=transform-functions-rotate3d_cart.png?size=webview" style="height: 47px; width: 510px;"></a><math> <mfenced><mtable><mtr><mtd>1<mo>+</mo>(1<mo>-</mo>cos(<mi>a</mi>))(<msup><mi>x</mi><mn>2</mn></msup><mo>-</mo>1)</mtd><mtd><mi>z</mi><mo>·</mo>sin(<mi>a</mi>)+<mi>x</mi><mi>y</mi>(1<mo>-</mo>cos(<mi>a</mi>))</mtd><mtd><mo>-</mo><mi>y</mi><mo>·</mo>sin(<mi>a</mi>)<mo>+</mo><mi>x</mi><mi>z</mi><mo>·</mo>(1<mo>-</mo>cos(<mi>a</mi>))</mtd></mtr><mtr><mtd><mo>-</mo><mi>z</mi><mo>·</mo>sin(<mi>a</mi>)<mo>+</mo><mi>x</mi><mi>y</mi><mo>·</mo>(1<mo>-</mo>cos(<mi>a</mi>))</mtd><mtd>1+(1-cos(a))(y2-1)</mtd><mtd><mi>x</mi><mo>·</mo>sin(<mi>a</mi>)<mo>+</mo><mi>y</mi><mi>z</mi><mo>·</mo>(1<mo>-</mo>cos(<mi>a</mi>))</mtd><mtr><mtd>ysin(a) + xz(1-cos(a))</mtd><mtd>-xsin(a)+yz(1-cos(a))</mtd><mtd>1+(1-cos(a))(z2-1)</mtd><mtd>t</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr> </mtr></mtable></mfenced></math></td>
   <td colspan="1"><a href="/@api/deki/files/5986/=transform-functions-rotate3d_hom4.png"><img src="/@api/deki/files/5986/=transform-functions-rotate3d_hom4.png?size=webview" style="height: 61px; width: 522px;"></a></td>
  </tr>
 </tbody>
</table>

<h3 id="rotateX()"><code>rotateX()</code></h3>

<p>The <code>rotateX()</code>CSS function defines a transformation that moves the element around the abscissa without deforming it. The amount of movement is defined by the specified angle; if positive, the movement will be clockwise, if negative, it will be counter-clockwise.</p>

<p>The axis of rotation passes by the origin, defined by {{ cssxref("transform-origin") }} CSS property.</p>

<p><code>rotateX(a)</code>is a shorthand for <code>rotate3D(1, 0, 0, a)</code>.</p>

<div class="note">In opposition to rotations in the plane, the composition of 3D rotations is usually not commutative; it means that the order in which the rotations are applied is crucial.</div>

<h4 id="表達式_6">表達式</h4>

<pre class="syntaxbox">rotateX(<em>a</em>)
</pre>

<h4 id="值_6">值</h4>

<dl>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle of the rotation. A positive angle denotes a clockwise rotation, a negative angle a counter-clockwise one.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1"><math> <mfenced><mtable><mtr><mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>cos(a)</mtd><mtd>-sin(a)</mtd></mtr><mtr><mtd>0</mtd><mtd>sin(a)</mtd><mtd>cos(a)</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1"><math><mfenced><mtable><mtr><mtd>1</mtd><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>cos(a)</mtd><mtd>-sin(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>sin(a)</mtd><mtd>cos(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="rotateY()"><code>rotateY()</code></h3>

<p>The <code>rotateY()</code>CSS function defines a transformation that moves the element around the ordinate without deforming it. The amount of movement is defined by the specified angle; if positive, the movement will be clockwise, if negative, it will be counter-clockwise.</p>

<p>The axis of rotation passes by the origin, defined by {{ cssxref("transform-origin") }} CSS property.</p>

<p><code>rotateY(a)</code>is a shorthand for <code>rotate3D(0, 1, 0, a)</code>.</p>

<div class="note">In opposition to rotations in the plane, the composition of 3D rotations is usually not commutative; it means that the order in which the rotations are applied is crucial.</div>

<h4 id="表達式_7">表達式</h4>

<pre class="syntaxbox">rotateY(<em>a</em>)
</pre>

<h4 id="值_7">值</h4>

<dl>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle of the rotation. A positive angle denotes a clockwise rotation, a negative angle a counter-clockwise one.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1"><math> <mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>0</mtd><mtd>sin(a)</mtd></mtr><mtr><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>-sin(a)</mtd><mtd>0</mtd><mtd>cos(a)</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1"><math><mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>0</mtd><mtd>sin(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>-sin(a)</mtd><mtd>0</mtd><mtd>cos(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="rotateZ()"><code>rotateZ()</code></h3>

<p>The <code>rotateZ()</code>CSS function defines a transformation that moves the element around the z-axis without deforming it. The amount of movement is defined by the specified angle; if positive, the movement will be clockwise, if negative, it will be counter-clockwise.</p>

<p>The axis of rotation passes by the origin, defined by {{ cssxref("transform-origin") }} CSS property.</p>

<p><code>rotateZ(a)</code>is a shorthand for <code>rotate3D(0, 0, 1, a)</code>.</p>

<div class="note">In opposition to rotations in the plane, the composition of 3D rotations is usually not commutative; it means that the order in which the rotations are applied is crucial.</div>

<h4 id="表達式_8">表達式</h4>

<pre class="syntaxbox">rotateZ(<em>a</em>)
</pre>

<h4 id="值_8">值</h4>

<dl>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle of the rotation. A positive angle denotes a clockwise rotation, a negative angle a counter-clockwise one.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>-sin(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>sin(a)</mtd><mtd>cos(a)</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math><mfenced><mtable><mtr><mtd>cos(a)</mtd><mtd>-sin(a)</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>sin(a)</mtd><mtd>cos(a)</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="scale()"><code>scale()</code></h3>

<p><img src="/@api/deki/files/5804/=transform-functions-scale_2_2.png?size=webview" style="float: left; height: 290px; width: 350px;"></p>

<p>The <code>scale()</code> CSS function modifies the size of the element. It can either augment or decrease its size and as the amount of scaling is defined by a vector, it can do so more in one direction than in another one.</p>

<p>This transformation is characterized by a vector whose coordinates define how much scaling is done in each direction. If both coordinates of the vector are equal, the scaling is uniform, or isotropic, and the shape of the element is preserved. In that case, the scaling function defines a homothetic transformation.</p>

<p>When outside the <code>]-1, 1[</code> range, the scaling enlarges the element in the direction of the coordinate; when inside the range, it shrinks the element in that direction. When equal to <code>1</code> it does nothing and when negative it performs a <em>point reflection</em> and the size modification.</p>

<div class="note">The <code>scale</code><code>()</code> function only applies the transformation in the Euclidian plane (in 2D). To scale in the space, the <code>scale3D()</code> function has to be used.</div>

<h4 id="表達式_9">表達式</h4>

<pre class="syntaxbox">scale(<em>sx</em>) or
scale(<em>sx</em>, <em>sy</em>)
</pre>

<h4 id="值_9">值</h4>

<dl>
 <dt><em>sx</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the abscissa of the scaling vector.</dd>
 <dt><em>sy</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the ordinate of the scaling vector. If not present, its default value is <em><strong>sx</strong></em>, leading to a uniform scaling preserving the shape of the element.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced> <mtable> <mtr><mtd>sx</mtd><mtd>0</mtd></mtr> <mtr><mtd>0</mtd><mtd>sy</mtd></mtr> </mtable> </mfenced> </math></td>
   <td><math> <mfenced><mtable><mtr>sx<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>sy</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>sx<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>sy</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>sx<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>sy</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[sx 0 0 sy 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="scale3d()"><code>scale3d()</code></h3>

<p>The <code>scale3d()</code> CSS function modifies the size of an element. Because the amount of scaling is defined by a vector, it can resize different dimensions at different scales.</p>

<p>This transformation is characterized by a vector whose coordinates define how much scaling is done in each direction. If all three coordinates of the vector are equal, the scaling is uniform, or isotropic, and the shape of the element is preserved. In that case, the scaling function defines a homothetic transformation.</p>

<p>When outside the <code>[-1, 1]</code> range, the scaling enlarges the element in the direction of the coordinate; when inside the range, it shrinks the element in that direction. When equal to <code>1</code> it does nothing and when negative it performs a <em>point reflection</em> and the size modification.</p>

<h4 id="表達式_10">表達式</h4>

<pre class="syntaxbox">scale3d(<em>sx</em>, <em>sy</em>, <em>sz</em>)
</pre>

<h4 id="值_10">值</h4>

<dl>
 <dt><em>sx</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the abscissa of the scaling vector.</dd>
 <dt><em>sy</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the ordinate of the scaling vector.</dd>
 <dt><em>sz</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the z-component of the scaling vector.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>sx<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>sy</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>sz</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>sx<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>sy</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>sz</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="scaleX()"><code>scaleX()</code></h3>

<p><img src="/@api/deki/files/5807/=transform-functions-scaleX_2.png?size=webview" style="float: left; height: 296px; width: 350px;">The <code>scaleX()</code> CSS function modifies the abscissa of each element point by a constant factor, except if this scale factor is <code>1</code>, in which case the function is the identity transform. The scaling is not isotropic and the angles of the element are not conserved.</p>

<p><code>scaleX(sx)</code> is a shorthand for <code>scale(sx, 1)</code> or for <code>scale3d(sx, 1, 1)</code>.</p>

<p><code>scaleX(-1)</code> defines an <a href="http://en.wikipedia.org/wiki/Axial_symmetry">axial symmetry</a> with a vertical axis passing by the origin (as specified by the <code><a href="transform-origin">transform-origin</a></code> property).</p>

<h4 id="表達式_11">表達式</h4>

<pre class="syntaxbox">scaleX(<em>s</em>)
</pre>

<h4 id="值_11">值</h4>

<dl>
 <dt><em>s</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the scaling factor to apply on the abscissa of each point of the element.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced> <mtable> <mtr><mtd>s</mtd><mtd>0</mtd></mtr> <mtr><mtd>0</mtd><mtd>1</mtd></mtr> </mtable> </mfenced> </math></td>
   <td><math> <mfenced><mtable><mtr>s<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>s<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>s<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[s 0 0 1 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="scaleY()"><code>scaleY()</code></h3>

<p><img src="/@api/deki/files/5967/=transform-functions-scaleY_2.png" style="float: left;"></p>

<p>The <code>scaleY()</code> CSS function modifies the ordinate of each element point by a constant factor except if this scale factor is <code>1</code>, in which case the function is the identity transform. The scaling is not isotropic and the angles of the element are not conserved.</p>

<p><code>scaleY(sy)</code> is a shorthand for <code>scale(1, sy)</code> or for <code>scale3d(1, sy, 1)</code>.</p>

<p><code>scaleY(-1)</code> defines an <a href="http://en.wikipedia.org/wiki/Axial_symmetry">axial symmetry</a> with a horizontal axis passing by the origin (as specified by the <code><a href="transform-origin">transform-origin</a></code> property).</p>

<h4 id="表達式_12">表達式</h4>

<pre class="syntaxbox">scaleY(s)
</pre>

<h4 id="值_12">值</h4>

<dl>
 <dt><em>s</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the scaling factor to apply on the ordinate of each point of the element.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd></mtr> <mtr><mtd>0</mtd><mtd>s</mtd></mtr> </mtable> </mfenced> </math></td>
   <td><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>s</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>s</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>s</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 0 0 s 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="scaleZ()"><code>scaleZ()</code></h3>

<p>The <code>scaleZ()</code> CSS function modifies the z-coordinate of each element point by a constant factor, except if this scale factor is <code>1</code>, in which case the function is the identity transform. The scaling is not isotropic and the angles of the element are not conserved.</p>

<p><code>scaleZ(sz)</code> is a shorthand for <code>scale3d(1, 1, sz)</code>.</p>

<p><code>scaleZ(-1)</code> defines an <a href="http://en.wikipedia.org/wiki/Axial_symmetry">axial symmetry</a> along the z-axis passing by the origin (as specified by the <code><a href="transform-origin">transform-origin</a></code> property).</p>

<h4 id="表達式_13">表達式</h4>

<pre class="syntaxbox">scaleZ(s)
</pre>

<h4 id="值_13">值</h4>

<dl>
 <dt><em>s</em></dt>
 <dd>Is a {{cssxref("&lt;number&gt;")}} representing the scaling factor to apply on the z-coordinate of each point of the element.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>s</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>s</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="skew()"><code>skew()</code></h3>

<p>The <code>skew()</code> CSS function is a shear mapping, or transvection, distorting each point of an element by a certain angle in each direction. It is done by increasing each coordinate by a value proportionate to the specified angle and to the distance to the origin. The more far from the origin, the more away the point is, the greater will be the value added to it.</p>

<h4 id="表達式_14">表達式</h4>

<pre class="syntaxbox">skew(<em>ax</em>)       <em>or</em>
skew(<em>ax</em>, <em>ay</em>)
</pre>

<h4 id="值_14">值</h4>

<dl>
 <dt><em>ax</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle to use to distort the element along the abscissa.</dd>
 <dt><em>ay</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle to use to distort the element along the ordinate.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>tan(ax)</mtd></mtr><mtr>tan(ay)<mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td><math> <mfenced><mtable><mtr>1<mtd>tan(ax)</mtd><mtd>0</mtd></mtr><mtr>tan(ay)<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr><mtr></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>tan(ax)</mtd><mtd>0</mtd></mtr><mtr>tan(ay)<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>tan(ax)</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>tan(ay)<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 tan(ay) tan(ax) 1 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="skewX()"><code>skewX()</code></h3>

<p>The <code>skewX()</code> CSS function is a horizontal shear mapping distorting each point of an element by a certain angle in the horizontal direction. It is done by increasing the abscissa coordinate by a value proportionate to the specified angle and to the distance to the origin. The more far from the origin, the more away the point is, the greater will be the value added to it.</p>

<h4 id="表達式_15">表達式</h4>

<pre class="syntaxbox">skewX(a)
</pre>

<h4 id="值_15">值</h4>

<dl>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle to use to distort the element along the abscissa.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>tan(ay)</mtd></mtr><mtr>0<mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td><math> <mfenced><mtable><mtr>1<mtd>tan(ay)</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>tan(ay)</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>tan(ay)</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 0 tan(a) 1 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="skewY()"><code>skewY()</code></h3>

<p>The <code>skewY()</code> CSS function is a vertical shear mapping distorting each point of an element by a certain angle in the vertical direction. It is done by increasing the ordinate coordinate by a value proportionate to the specified angle and to the distance to the origin. The more far from the origin, the more away the point is, the greater will be the value added to it.</p>

<h4 id="表達式_16">表達式</h4>

<pre class="syntaxbox">skewY(a)
</pre>

<h4 id="值_16">值</h4>

<dl>
 <dt><em>a</em></dt>
 <dd>Is an {{ cssxref("&lt;angle&gt;") }} representing the angle to use to distort the element along the ordinate.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd></mtr><mtr>tan(ax)<mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>tan(ax)<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>tan(ax)<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>tan(ax)<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 tan(a) 0 1 0 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="translate()"><code>translate()</code></h3>

<p><img src="/@api/deki/files/5970/=transform-functions-translate_2.png" style="float: left;">The <code>translate()</code> CSS function moves the position of the element on the plane. This transformation is characterized by a vector whose coordinates define how much it moves in each direction.</p>

<h4 id="Syntax">Syntax</h4>

<pre class="syntaxbox">translate(tx)       <em>or</em>
translate(tx, ty)
</pre>

<h4 id="值_17">值</h4>

<dl>
 <dt><em>tx</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the abscissa of the translating vector.</dd>
 <dt><em>ty</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the ordinate of the translating vector. If missing, it is assumed to be equals to <strong>tx</strong> :  <code>translate(2)</code> means <code>translate(2, 2)</code>.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2">
    <p>A translation is not a linear transform in ℝ<sup>2</sup> and cannot be represented using a matrix in the cartesian coordinates system.</p>
   </td>
   <td><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>tx</mtd></mtr><mtr>0<mtd>1</mtd><mtd>ty</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>tx</mtd></mtr><mtr>0<mtd>1</mtd><mtd>ty</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>tx</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>ty</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 0 0 1 tx ty]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="translate3d()"><code>translate3d()</code></h3>

<p>The <code>translate3d()</code> CSS function moves the position of the element in the 3D space. This transformation is characterized by a 3-dimension vector whose coordinates define how much it moves in each direction.</p>

<h4 id="表達式_17">表達式</h4>

<pre class="syntaxbox">translate3d(tx, ty, tz)
</pre>

<h4 id="值_18">值</h4>

<dl>
 <dt><em>tx</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the abscissa of the translating vector.</dd>
 <dt><em>ty</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the ordinate of the translating vector.</dd>
 <dt><em>tz</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the z component of the translating vector. It can't be a {{cssxref("&lt;percentage&gt;")}} value; in that case the property containing the transform is considered invalid.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">
    <p>This transform applies to the 3D space and cannot be represented on the plane.</p>
   </td>
   <td colspan="1" rowspan="2">A translation is not a linear transform in ℝ<sup>3</sup> and cannot be represented using a matrix in the Cartesian coordinates system.</td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>tx</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>ty</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>tz</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<h3 id="translateX()"><code>translateX()</code></h3>

<p><img src="/@api/deki/files/5972/=transform-functions-translateX_2.png" style="float: left;">The <code>translateX()</code> CSS function moves the element horizontally on the plane. This transformation is characterized by a {{cssxref("&lt;length&gt;")}} defining how much it moves horizontally.</p>

<p><code>translateX(tx)</code> is a shortcut for <code>translate(tx, 0)</code>.</p>

<h4 id="表達式_18">表達式</h4>

<pre class="syntaxbox">translateX(t)
</pre>

<h4 id="值_19">值</h4>

<dl>
 <dt><em>t</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the abscissa of the translating vector.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2">
    <p>A translation is not a linear transform in ℝ<sup>2</sup> and cannot be represented using a matrix in the cartesian coordinates system.</p>
   </td>
   <td><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>t</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>t</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>t</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 0 0 1 t 0]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="translateY()"><code>translateY()</code></h3>

<p><img src="/@api/deki/files/5971/=transform-functions-translateY_2.png" style="float: left;">The <code>translateY()</code> CSS function moves the element vertically on the plane. This transformation is characterized by a {{cssxref("&lt;length&gt;")}} defining how much it moves vertically.</p>

<p><code>translateY(ty)</code> is a shortcut for <code>translate(0, ty)</code>.</p>

<h4 id="Syntax_2">Syntax</h4>

<pre class="syntaxbox">translateY(t)
</pre>

<h4 id="值_20">值</h4>

<dl>
 <dt><em>t</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the ordinate of the translating vector.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="1" rowspan="2">
    <p>A translation is not a linear transform in ℝ<sup>2</sup> and cannot be represented using a matrix in the cartesian coordinates system.</p>
   </td>
   <td><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>t</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
   <td colspan="1" rowspan="2"><math> <math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>t</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></math></td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>t</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
  <tr>
   <td><code>[1 0 0 1 0 t]</code></td>
  </tr>
 </tbody>
</table>

<h3 id="translateZ()"><code>translateZ()</code></h3>

<p>The <code>translateZ()</code> CSS function moves the element along the z-axis of the 3D space. This transformation is characterized by a {{cssxref("&lt;length&gt;")}} defining how much it moves.</p>

<p><code>translateZ(tz)</code> is a shorthand for <code>translate3d(0, 0, tz)</code>.</p>

<h4 id="表達式_19">表達式</h4>

<pre class="syntaxbox">translateZ(t)
</pre>

<h4 id="值_21">值</h4>

<dl>
 <dt><em>t</em></dt>
 <dd>Is a {{cssxref("&lt;length&gt;")}} representing the z-component of the translating vector. It can't be a {{cssxref("&lt;percentage&gt;")}} value; in that case the property containing the transform is considered invalid.</dd>
</dl>

<table>
 <thead>
  <tr>
   <th scope="col">Cartesian coordinates on ℝ<sup>2</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>2</sup></th>
   <th scope="col">Cartesian coordinates on ℝ<sup>3</sup></th>
   <th scope="col">Homogeneous coordinates on ℝℙ<sup>3</sup></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colspan="2" rowspan="2">This transform applies to the 3D space and cannot be represented on the plane.</td>
   <td colspan="1" rowspan="2">A translation is not a linear transform in ℝ<sup>3</sup> and cannot be represented using a matrix in the Cartesian coordinates system.</td>
   <td colspan="1" rowspan="2"><math> <mfenced><mtable><mtr>1<mtd>0</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr>0<mtd>1</mtd><mtd>0</mtd><mtd>0</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd><mtd>t</mtd></mtr><mtr><mtd>0</mtd><mtd>0</mtd><mtd>0</mtd><mtd>1</mtd></mtr></mtable> </mfenced> </math></td>
  </tr>
 </tbody>
</table>

<p> </p>