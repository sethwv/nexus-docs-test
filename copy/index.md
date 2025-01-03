<body onload="
    (function() {
        const searchParams = window.location.search.substring(1); // Remove the leading '?'
        const copy = searchParams ? decodeURIComponent(searchParams) : ''; // Decode and assign
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
