---
toc: false
comments: false
layout: post
title: ITunes genre project
description: User can type in a song, program will return songs in that genre
courses: { compsci: {week: 3} }
type: tangibles
---

<div>
  <input type="text" id="filterInput" placeholder="Enter song">
  <button onclick="fetchData()">Search</button>
</div>

<table>
  <thead>
    <tr>
      <th>Artist</th>
      <th>Track</th>
      <th>Images</th>
      <th>Preview</th>
    </tr>
  </thead>
  <tbody id="result">
    <!-- generated rows -->
  </tbody>
</table>

<script>
  fetch(url, headers)
      .then(response => {
        // check for response errors
        if (response.status !== 200) {
          const errorMsg = 'Database response error: ' + response.status;
          console.log(errorMsg);
          const tr = document.createElement("tr");
          const td = document.createElement("td");
          td.innerHTML = errorMsg;
          tr.appendChild(td);
          resultContainer.appendChild(tr);
          return;
        }
</script>