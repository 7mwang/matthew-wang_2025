---
layout: base
title: Student Home 
description: Home Page
hide: true
---

<div class="dropdown">
<button class="dropbtn">Lost? Check one of these out! ↓</button>
<div class = "dropdown-content">
<a href="{{site.baseurl}}/2024/09/08/javascript-cell_IPYNB_2_.html">Javascript Cell</a>
<a href="{{site.baseurl}}/2024/09/08/plans_IPYNB_2_.html">Plans and Accomplishments</a>
<a href="{{site.baseurl}}/about/">About Me</a>
</div>
</div>

Matthew Wang's site for CSA 2025!

<button onclick = "showLangs()">Code code code...code?</button>
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQEc9A_S6BPxCDRp5WjMFEfXrpCu1ya2OO-Lw&s" style="width:200px; height:auto" class = "lang">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/1200px-Unofficial_JavaScript_logo_2.svg.png" style="width:200px; height:auto" class = "lang">
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTkQqh5ldA3rAHmQZd7zeovoc-4w0xBZ_ZxCw&s" style="width:200px; height:auto" class = "lang">
<p class = "lang"></p>
<img src="{{site.baseurl}}/images/new_foe_java.png" style="width:800px; height:auto" class = "lang">

<script>
var languages = document.getElementsByClassName("lang")
addEventListener("load", (event) => {
    for (var i = 0; i < languages.length; i++) {
        languages[i].style.display = "none"
    }
})

function showLangs() {
    for (var i = 0; i < languages.length; i++) {
        if (languages[i].style.display != "block") {
            languages[i].style.display = "block" 
        }
        else {
            languages[i].style.display = "none"
        }
    }
}
</script>    