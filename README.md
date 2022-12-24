# learning-mermaid

Learning how to use Mermaid with Vue.js

# How to use

Just install the packages and start the dev server:

```bash
npm install
npm run dev
```

Or the online demo: [GitHub Pages Demo](https://hehuan2112.github.io/learning-mermaid/).

# What I learnt
In short, for static figures, just follow the example on official website.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
  </head>
  <body>
    <pre class="mermaid">
  graph LR
      A --- B
      B-->C[fa:fa-ban forbidden]
      B-->D(fa:fa-spinner);
    </pre>
    <script type="module">
      import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@9/dist/mermaid.esm.min.mjs';
      mermaid.initialize({ startOnLoad: true });
    </script>
  </body>
</html>
```

If more dynamic features are needed to customized the diagram on the fly, `mermaid.render()` could be better:

```JavaScript
mermaid.render(
    'what',
    props.chart_code, 
    (svgCode) => {
        // the svgCode contains the generated SVG
        // you can update the innerHTML of a DIV
        // such as `document.querySelector('#mermaid_chart').innerHTML = svgCode`
        // usually it's OK, and you can get what you want.
        
        // for this example code, the diagram can be updated by changing a Vue's attribute,
        // which is binded to an innerHTML of a DIV.
        mermaid_svg.value = svgCode;
    }
);
```

More details can be found in the [MFC.vue] code.

Need to customize the Vue component for flowchart if needed.