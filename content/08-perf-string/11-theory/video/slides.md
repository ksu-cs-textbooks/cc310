---
type: "reveal"
hidden: true
---


<section>
<img class="stretch plain" src="/images/0/core-logo-on-white.svg">
<h3> Module 1 <br> Strings and StringBuilders <br> Immutable</h3>
<hr style="height:15px;color:512888;background-color:512888;">
<h4>CC315</h4>
</section>

<section>
<h3> Strings </h3>
<pre class="" style="font-size: .3em"><code class="python"> s = "Go Cats!"</code></pre>
<pre class="" style="font-size: .3em"><code class="python"> t = "123!?~ k\n foo" #\n is new line character</code></pre>
<pre class="" style="font-size: .3em"><code class="python"> u = ":)"</code></pre>
</section>

<section>
<h3> Strings </h3>
<img class="stretch plain" src="/images/13/315Basic.png">
</section>

<section>
<h3> Strings </h3>
<pre class="" style="font-size: .3em"><code class="python"> RESULT = "Go Cats!"</code></pre>
<img class="stretch plain" src="/images/13/315Basic.png">
</section>



<section>
	<h3>Sample Algorithm</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)
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
</section>

<section>
	<h3>Sample Algorithm</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)
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
 <pre class="" style="font-size: .3em"><code class="python"> ENCODER("Fish",2) = "Hkuj"</code></pre>
</section>


<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Data is great!",8)
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
 	<img class="stretch plain" src="/images/13/315mem_map.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Data is great!",8)
        //TEXT is the text to encode
        //X is the offset
        <mark>ENC = ""</mark>
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
 	<img class="stretch plain" src="/images/13/315mem_map1.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("<mark>D</mark>ata is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        <mark>loop I from 1 to LENGTH of TEXT</mark>
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
 	<img class="stretch plain" src="/images/13/315mem_map1.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("<mark>D</mark>ata is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
           <mark> CURRENT = TEXT[I]</mark>
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC += CHAR_ENC
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map1.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("<mark>D</mark>ata is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            <mark>IF CURRENT IS A LETTER</mark>
                CHAR_ENC = GET X-th CHAR after CURRENT
                ENC += CHAR_ENC
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map1.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("<mark>D</mark>ata is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                <mark>CHAR_ENC = GET X-th CHAR after CURRENT</mark> # D -> L
                ENC += CHAR_ENC
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map1.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("<mark>D</mark>ata is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC += CHAR_ENC</mark>
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map2.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("D<mark>a</mark>ta is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        <mark>loop I from 1 to LENGTH of TEXT</mark>
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
 	<img class="stretch plain" src="/images/13/315mem_map2.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("D<mark>a</mark>ta is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                <mark>CHAR_ENC = GET X-th CHAR after CURRENT</mark> # a -> h
                ENC += CHAR_ENC
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map2.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("D<mark>a</mark>ta is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC += CHAR_ENC</mark>
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map3.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Da<mark>t</mark>a is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        <mark>loop I from 1 to LENGTH of TEXT</mark>
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
 	<img class="stretch plain" src="/images/13/315mem_map3.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Da<mark>t</mark>a is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC += CHAR_ENC</mark>
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map3.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Da<mark>t</mark>a is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        loop I from 1 to LENGTH of TEXT
            CURRENT = TEXT[I]
            IF CURRENT IS A LETTER
                CHAR_ENC = GET X-th CHAR after CURRENT
                <mark>ENC += CHAR_ENC</mark>
            ELSE
                ENC += '*'
        end loop
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map4.png">
</section>

<section>
	<h3>Walk Through</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Dat<mark>a</mark> is great!",8)
        //TEXT is the text to encode
        //X is the offset
        ENC = ""
        <mark>loop I from 1 to LENGTH of TEXT</mark>
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
 	<img class="stretch plain" src="/images/13/315mem_map4.png">
</section>

<section>
	<h3>Fast Forward</h3>
    <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)                #Call: ENCODER("Data is great<mark>!</mark>",8)
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
        <mark>end loop</mark>
        return ENC
    end function
 </code></pre>
 	<img class="stretch plain" src="/images/13/315mem_map5.png">
</section>


<section>
<h3>Fast Forward</h3>
  <div style="float: right; width: 58%">
	       <pre class="" style="font-size: .3em"><code class="python">
    function ENCODER(TEXT,X)
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
  <div style="float:left; width: 42%">
<small>

| Iterations | Char <br/>Copies | Mem. <br/> Adr. |
| --- | --- | --- |
| 1 | 1 | 2 |
| 2 | 3 (1+2) | 3 |
| 3 | 6 (3+3) | 4 |
| 4 | 10 (6+4) | 5 |
| 5 | 15 (10+5) | 6 |

</small>
  </div>
</section>

<section>
<h3>Fast Forward</h3>
<small>

| Iterations | Char <br/>Copies | Mem. <br/> Adr. |
| --- | --- | --- |
| 1 | 1 | 2 |
| 2 | 3 (1+2) | 3 |
| 3 | 6 (3+3) | 4 |
| 4 | 10 (6+4) | 5 |
| 5 | 15 (10+5) | 6 |
| n | (n(n+1))/2 | n + 1|


</small>
</section>


<section>
	<h3>Fast Forward</h3>

<small>

| Iterations | Char <br/>Copies | Memory <br/> Addresses |
| --- | --- | --- |
| 1 | 1 | 2 |
| 2 | 3 (1+2) | 3 |
| 3 | 6 (3+3) | 4 |
| 4 | 10 (6+4) | 5 |
| 5 | 15 (10+5) | 6 |
| n | (n(n+1))/2 | n + 1|
| 1,000,000 | 500,000,500,000 | 1,000,001|

</small>
</section>


