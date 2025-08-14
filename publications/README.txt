# Publications (newest first)
Each Markdown file now includes explicit `date: YYYY-12-31` and `lastmod` fields.
Use this template for the publications list to sort by `.Date` descending:

layouts/publications/list.html
--------------------------------
{{ define "main" }}
<section class="section">
  <h1>Publications</h1>
  {{ range (where .Pages "Section" "publications").ByDate.Reverse }}
    <article class="pub-line">
      <h3><a class="link-underline" href="{{ .RelPermalink }}">{{ .Title }}</a></h3>
      <p class="muted">
        {{ .Params.authors }} ({{ .Params.year }}) — <em>{{ .Params.journal }}</em>
        {{ with .Params.volume }} {{ . }}{{ end }} {{ with .Params.pages }}: {{ . }}{{ end }}
        {{ with .Params.doi }} · <a href="{{ . }}">DOI</a>{{ end }}
        {{ with .Params.pdf }} · <a href="{{ . }}">PDF</a>{{ end }}
      </p>
    </article>
  {{ end }}
</section>
{{ end }}
