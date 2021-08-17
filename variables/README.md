### In below example - release will throw exception since its wrapped in  {{- with .Values.favorite }}. We can access it via setting variables.

```
 {{- $relname:= .Release.Name -}}
  {{- with .Values.favorite }}
  drink: {{ .drink | upper | quote }}
  food: {{ .food | upper | quote }}
  release: {{ $relname }}
  {{- end }}
```

### Variable in range

```
{{- range $index, $toppings := .Values.pizzaToppings }}
      {{ $index }}: {{$toppings}}
    {{- end }}
```
