<script>
	import hljs from 'highlight.js';
	let code = '\n<pre>\n\t<code>{code}</code>\n</pre>';
	$: codeFormated = hljs.highlight(code, { language: 'html' }).value;
</script>

<!-- Один блок с contenteditable='true' с прозрачным фоном, поверх другого блока -->
<div class="position-relative">
	<pre class="form-control position-absolute" style="min-height:20em">
        {@html codeFormated}
    </pre>

	<pre
		class="form-control position-absolute"
		style="min-height:20em; background-color:transparent; color:transparent;caret-color: black"
		contenteditable="true"
		bind:innerText={code}
	/>
</div>
