---
toc: true
comments: true
layout: post
title: Song Recommender
courses: { compsci: {week: 3} }
type: tangibles
---

<head>
    <title>iTunes Search API</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <style>
        .result {
            display: inline-block;
            background-color: black;
            color: white;
            border-radius: 25px;
            padding: 10px;
            margin: 10px;
            width: 100%;
        }
        .result img {
            vertical-align: middle;
            margin-right: 10px;
        }
    </style>
</head>
<body>
    <h1>iTunes Search API</h1>
    <input type="text" id="search" placeholder="Search">
    <button id="search-button">Search</button>
    <div id="results"></div>
    <script>
    function searchItunesByGenre(genre, callback) {
        const baseUrl = "https://itunes.apple.com/search";
        const params = new URLSearchParams({
            term: genre,
            media: "music",
            entity: "song",
            attribute: "genreTerm"
        });
        fetch(`${baseUrl}?${params.toString()}`)
            .then(response => response.json())
            .then(data => {
                callback(data.results);
            })
            .catch(error => {
            console.error("An error occurred while searching the iTunes Store:", error);
            });
        }
        function displayResults(results) {
        $('#results').empty();
        results.forEach(result => {
            var $result = $('<div class="result"></div>');
            $result.append('<img src="' + result.artworkUrl100 + '">');
            $result.append('<br> <span>' + result.collectionName + '</span><br>');
            $result.append('<span>' + result.artistName + '</span><br>');
            $result.append('<span>' + result.primaryGenreName + '</span><br>');
            $('#results').append($result);
        });
    }
    </script>
    <script>
        $(document).ready(function() {
            $('#search-button').click(function() {
                var searchTerm = $('#search').val();
                $.ajax({
                    url: 'https://itunes.apple.com/search?term=' + searchTerm,
                    dataType: 'jsonp',
                    success: function(data) {
                        $('#results').empty();
                        data.results.forEach(function(result) {
                            var $result = $('<div class="result"></div>');
                            $result.append('<img src="' + result.artworkUrl100 + '">');
                            $result.append('<br> <span>' + result.collectionName + '</span><br>');
                            $result.append('<span>' + result.artistName + '</span><br>');
                            $result.append('<span>' + result.primaryGenreName + '</span><br>');
                            var $findSimilarButton = $('<button>Find Similar Results</button>');
                            $findSimilarButton.click(function() {
                                var genre = result.primaryGenreName;
                                var genreSearch = searchItunesByGenre(genre, displayResults);
                            });
                            $result.append($findSimilarButton);
                            $('#results').append($result);
                        });
                    }
                });
            });
        });
    </script>
</body>