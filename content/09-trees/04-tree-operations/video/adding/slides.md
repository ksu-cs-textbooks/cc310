---
type: "reveal"
hidden: true
---

<section>
<img class="stretch plain" src="/images/14/core-logo-on-white.png">
<h3> Module 2 <br> Trees <br> Add Child</h3>
<hr style="height:15px;color:512888;background-color:512888;">
<h4>CC315</h4>
</section>

<section>
<img class="stretch plain" src="/images/14/315_add_child1.svg">
</section>

<section>
<table>
<tr><td> MyTree </td><td> parent </td><td> children </td><td> item </td></tr>
<tr><td> a </td><td> none </td><td> {b,c} </td><td> A </td></tr>
<tr><td> b </td><td> a </td><td> {d} </td><td> B </td></tr>
<tr><td> c </td><td> a </td><td> {} </td><td> C </td></tr>
<tr><td> d </td><td> b </td><td> {} </td><td> D </td></tr>
<tr><td> x </td><td> none </td><td> {y,z} </td><td> X </td></tr>
<tr><td> y </td><td> x </td><td> {} </td><td> Y </td></tr>
<tr><td> z </td><td> x </td><td> {} </td><td> Z </td></tr>
</table>
</section>

<section>
<table>
<tr><td> MyTree </td><td> parent </td><td> children </td><td> item </td></tr>
<tr><td> a </td><td> none </td><td> {b,c} </td><td> A </td></tr>
<tr><td> b </td><td> a </td><td> {d} </td><td> B </td></tr>
<tr><td> c </td><td> a </td><td> {<mark>x</mark>} </td><td> C </td></tr>
<tr><td> d </td><td> b </td><td> {} </td><td> D </td></tr>
<tr><td> x </td><td><mark> c </mark></td><td> {y,z} </td><td> X </td></tr>
<tr><td> y </td><td> x </td><td> {} </td><td> Y </td></tr>
<tr><td> z </td><td> x </td><td> {} </td><td> Z </td></tr>
</table>
</section>

<section>
<img class="stretch plain" src="/images/14/315_add_child2.svg">
</section>

<section>
<h3>Special Considerations</h3>
<ul>
<li>Child can't already have parent</li>
<li>Child can't be a child of attempted parent</li>
</ul>
</section>


<section>
<h3>Pseudocode</h3>
<pre class="" style="font-size: .3em;width: 600"><code class="python">
function ADDCHILD(CHILD)
    IF CHILD has PARENT
        throw exception
    IF CHILD is CHILD of PARENT
        return FALSE
    ELSE
        append CHILD to PARENT`s children
        set CHILD`s parent to PARENT
        return TRUE
end function
 </code></pre>
</section>
