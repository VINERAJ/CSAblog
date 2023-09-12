---
toc: true
comments: true
layout: post
title: JavaScript Experiments
description: Learning javascript output
courses: { compsci: {week: 4} }
type: tangibles
---
<head>
    <title>Javascript Experiments</title>
    <table></table>
    <script>
        var create = document.createElement('BUTTON')
    </script>
</head>

<script>
    let people = [
        { name: "Vinay", age: "17", grade: "12" },
    ];

    function generateTable(table, data) {
        let thead = table.createTHead();
        let row = thead.insertRow();
        for (let key of data) {
            let th = document.createElement("th");
            let text = document.createTextNode(key);
            th.appendChild(text);
            row.appendChild(th);
        }
        for (let element of people) {
        let dataRow = table.insertRow();
        for (key in element) {
        let cell = dataRow.insertCell();
        let text = document.createTextNode(element[key]);
        cell.appendChild(text);
        }
    }
    }

    let table = document.querySelector("table");
    let data = Object.keys(people[0]);
    generateTable(table, data);
</script>