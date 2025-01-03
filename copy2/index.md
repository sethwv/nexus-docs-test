---
layout: default
title: Copy Test
nav_order: 99
search_exclude: true
---

<style>
    code {
        font-family: 'Consolas', Courier, monospace;
        background-color: #333;
        padding: 10px;
        border-radius: 10px;
        box-shadow: 1px 1px 10px #222 inset;
    }

    .content {
        background-color: #444 !important;
        padding: 20px;
        border-radius: 10px;
        box-shadow: 1px 1px 10px #222;
    }
</style>

<script language="javascript" type="text/javascript">
    function doScript() {
        const searchParams = new URLSearchParams(window.location.search);
        const copy = searchParams.get('copy');

        document.getElementById("copy").innerHTML = copy;
    }


    function doCopy(string) {
        // navigator.permissions.query({ name: "clipboard-write" }).then((result) => {
        //     if (result.state === "granted" || result.state === "prompt") {
        //         navigator.clipboard.writeText(string).then(function() {
        //         console.log('Async: Copying to clipboard was successful!');
        //     }, function(err) {
        //         console.error('Async: Could not copy text: ', err);
        //     });
        //   }
        // });
        const textArea = document.createElement('textarea');
        textArea.value = document.getElementById("copy").innerHTML;
        textArea.style.opacity = 0;
        document.body.appendChild(textArea);
        textArea.focus();
        textArea.select();
        try {
            const success = document.execCommand('copy');
            alert(`${success ? `Success! Copied ${textArea.value} to clipboard.` : 'Something went wrong, please manually copy.'}`);
        } catch (err) {
            console.error(err.name, err.message);
        }
        document.body.removeChild(textArea);


    }
</script>


<div class="content" onclick="doCopy()">
    <h1>Click/Tap here to copy <code id="copy"></code> to clipboard.</h1>
</div>
