---
layout:     post
title:      Get Spotify playlist cover image with JavaScript
category:   misc
author:     Tiantian Li
---

This is just a very ugly attempt to embed JavaScript in a markdown file.

Thanks to Spotify Web API, the whole procedure is quite simple. The only thing you need to do is to get the playlist ID from the playlist link and then send a request to the API.

The access token is obtained from my tiny server, which is just a simple Node.js app that returns a token every time it receives a request. The token is valid for 1 hour. Hope it won't be abused.

## Demo

<!--
// make text input field and button
-->
<input type="text" id="input" value="spotify playlist link here" />
<button id="button">click me to get the cover</button>

<img id="image" src="" />

<!--
// by extracting the playlist ID from the input field, send a request to the API and get the cover image
// get a access token first
-->
<script>
    var input = document.getElementById("input");
    var button = document.getElementById("button");
    var image = document.getElementById("image");

    button.onclick = function() {
        var playlistID = input.value.split("/")[4];
        var url = "https://api.spotify.com/v1/playlists/" + playlistID + "/images";

        // first, get a token from rn.arcohol.com
        var token = "";
        var tokenRequest = new XMLHttpRequest();
        tokenRequest.open("GET", "https://rn.arcohol.com/", true);
        tokenRequest.send();
        tokenRequest.onreadystatechange = function() {
            if (tokenRequest.readyState == 4 && tokenRequest.status == 200) {
                token = JSON.parse(tokenRequest.responseText).access_token;
                // then, send a request to the API
                var request = new XMLHttpRequest();
                request.open("GET", url, true);
                request.setRequestHeader("Authorization", "Bearer " + token);
                request.send();
                request.onreadystatechange = function() {
                    if (request.readyState == 4 && request.status == 200) {
                        var response = JSON.parse(request.responseText);
                        // display the cover image
                        image.src = response[0].url;
                    }
                }
            }
        }
    }
</script>

## Reference

- [Spotify Web API](https://developer.spotify.com/documentation/web-api/)
