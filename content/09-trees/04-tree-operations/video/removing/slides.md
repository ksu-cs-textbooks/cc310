---
type: "reveal"
hidden: true
---

<section>
<img class="stretch plain" src="/images/14/core-logo-on-white.png">
<h3> Module 2 <br> Trees <br> Remove Child</h3>
<hr style="height:15px;color:512888;background-color:512888;">
<h4>CC315</h4>
</section>

<section>
<img class="stretch plain" src="/images/14/315trash.svg">
	<p class="imagecredit">Image Credit: <a href="https://freesvg.org/trash-folder">FreeSVG</a></p>
</section>

<section>
<img class="stretch plain" src="/images/14/315_add_child2.svg">
</section>

<section>
<table>
<tr><td> MyTree </td><td> parent </td><td> children </td><td> item </td></tr>
<tr><td> a </td><td> none </td><td> {b,c} </td><td> A </td></tr>
<tr><td> b </td><td> a </td><td> {d} </td><td> B </td></tr>
<tr><td> c </td><td> a </td><td> {x} </td><td> C </td></tr>
<tr><td> d </td><td> b </td><td> {} </td><td> D </td></tr>
<tr><td> x </td><td> c </td><td> {y,z} </td><td> X </td></tr>
<tr><td> y </td><td> x </td><td> {} </td><td> Y </td></tr>
<tr><td> z </td><td> x </td><td> {} </td><td> Z </td></tr>
</table>
</section>

<section>
<table>
<tr><td> MyTree </td><td> parent </td><td> children </td><td> item </td></tr>
<tr><td> a </td><td> none </td><td> {b,c} </td><td> A </td></tr>
<tr><td> b </td><td> a </td><td> {d} </td><td> B </td></tr>
<tr><td> c </td><td> a </td><td> <mark>{}</mark> </td><td> C </td></tr>
<tr><td> d </td><td> b </td><td> {} </td><td> D </td></tr>
<tr><td> x </td><td> <mark>none</mark> </td><td> {y,z} </td><td> X </td></tr>
<tr><td> y </td><td> x </td><td> {} </td><td> Y </td></tr>
<tr><td> z </td><td> x </td><td> {} </td><td> Z </td></tr>
</table>
</section>

<section>
<img class="stretch plain" src="/images/14/315_add_child1.svg">
</section>

<section>
<h3>Special Considerations</h3>
<ul>
<li>Node should be child of parent</li>
</ul>
</section>

<section>
<h3>Pseudocode</h3>
<pre class="" style="font-size: .3em;width: 600"><code class="python">
function REMOVECHILD(CHILD)
    IF CHILD in PARENT`S children
        REMOVE CHILD from PARENT`s children
        SET CHILD`s PARENT to NONE
        return TRUE
    ELSE
        return FALSE
end function
 </code></pre>
</section>
