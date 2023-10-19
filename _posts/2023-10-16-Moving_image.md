---
toc: true
comments: true
layout: post
title: Moving Image
description: Learning javascript output
courses: { compsci: {week: 9} }
type: tangibles
---

<head>
    <title>Moving Image</title>
</head>
<body>
    <img src="/CSAblog/images/logo.png" id = "image" alt="drawing" width="200"/>
    <button class="move-button" id="move-button" style="height:20px;width:150px">Move the image!</button>
    <script>
        function move() {
            var running = "true";
            var x = document.getElementById("image").offsetLeft;
            var y = document.getElementById("image").offsetTop;
            document.getElementById("image").style.marginLeft = (x+5) + 'px';
            document.getElementById("image").style.marginTop = (y+5) + 'px';
        }
        while (running=="true") {
            move();
        }
    </script>
</body>