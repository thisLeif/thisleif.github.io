<!DOCTYPE html>
<html>
<body>

<figure>
    <svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
        <circle cx="42" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" /></svg>
    <figcaption>test</figcaption>
</figure>

<pre class="mermaid" id="dependency">
  graph LR
      A --- B
      B-->C[fa:fa-ban forbidden]
      B-->D(fa:fa-spinner);
    </pre>
<script type="module">
      import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';
    </script>

</body>
</html>