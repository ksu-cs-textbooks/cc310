---
type: "reveal"
hidden: true
---


<section>
<img class="stretch plain" src="/images/0/core-logo-on-white.svg">
<h3> Module 1 <br> Strings and StringBuilders <br> Memory Analysis</h3>
<hr style="height:15px;color:512888;background-color:512888;">
<h4>CC315</h4>
</section>

<section>
<h3> Where We Are </h3>
<ul>
<li> Strings are  natural choice</li>
<li> Strings are immutable </li>
<li> We can work around that </li>
<ul>
<li> Java: StringBuilder Class </li>
<li> Python: Array </li>
</ul>
</ul>
</section>


<section>
<h5>Psuedocode Comparison</h5>
<div>
<pre class="" style="font-size: .2em; width: 35%"><code class="java">
    function ENCODER(TEXT,X) // General: Strings
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC += CHAR_ENC
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
</div>
<div style="width:100%">
<div style="float:left">
 <pre class="" style="font-size: .2em;width:100%"><code class="java">
    function SBENCODER(TEXT,X) // Java: StringBuilder
        //TEXT is the text to encode
        //X is the offset
        ENC = new StringBuilder()
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        end loop
        return ENC.toString()
    end function
 </code></pre>
</div>
<div style="float:right">
 <pre class="" style="font-size: .2em;width:100%"><code class="python">
    function ARR_ENCODER(TEXT,X) # Python: Array
        #TEXT is the text to encode
        #X is the offset
        ENC = []
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC.append(CHAR_ENC)
            ELSE
                ENC.append('*')
        end loop
        return "".join(ENC)
    end function
 </code></pre>
 </div>
 </div>
</section>



<section>
	<h3> Time Comparison</h3>
<div class="row">
    <img src="/images/13/315_stringsTime_python.png" style="width:48%">
    <img src="/images/13/315_stringsTime_java.png" style="width:48%">
</div>
</section>


<section>
<h3> Memory Analysis </h3>
<ul>
<li> Language garbage collection </li>
<li> Language's compensation <br/>for immutable strings </li>
<li> Where does that leave us? </li>
</ul>
</section>

<section>
<h3> To String or Not To String</h3>
<ul>
<li> Good: Strings are okay </li>
<li> Bad: String modification </li>
<li> It depends!</li>
</ul>
</section>

