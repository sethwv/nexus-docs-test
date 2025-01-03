---
layout: default
title: Copy Code
nav_order: 99
search_exclude: true
nav_exclude: true
---

<style>
    code {
        font-family: 'Consolas', Courier, monospace;
        background-color: #FFF;
        padding: 8px !important;
        border-radius: 3px;
        /* box-shadow: 1px 1px 2px #222 inset; */
    }

    .content {
        /* background-color: #AAA !important; */
        padding: 20px;
        /* border-radius: 10px; */
        /* box-shadow: 1px 1px 10px #AAA; */
    }
</style>

<body onload="
    (function() {
        const searchParams = new URLSearchParams(window.location.search);
        const copy = searchParams.get('code');
        document.getElementById('copy').innerHTML = copy;
    })();
">
    <div class="main">
        <div class="content" onclick="
            (function() {
                const textArea = document.createElement('textarea');
                textArea.value = document.getElementById('copy').innerHTML;
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
            })();
        ">
            <h1>Click or tap here to copy <code id="copy"></code> to your clipboard.</h1>
        </div>
    </div>
</body>
