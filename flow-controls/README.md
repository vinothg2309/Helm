# Flow Controls

1. if/else
2. With

## Commenting

If we comment yaml with 

- '#' - helm won't ignore it & will display it in rendered template
- {{/* */}} - helm will ignore it while rendering template


## if-else

### Condition is evaluated to false if the value is
    - a boolean false
    - a numeric 0
    - an empty string
    - a nil (empty or null)
    - an empty collection (map, slice, tuple, dict, array)

## With

- It controls variable scoping
- '.' is a references to the current scope
- Syntax is similar to if condition

```
 {{ with PIPELINE }}
  #restricted scope
 {{ end }}
```
### We can't use anyother object available in Values.yaml except the one which is mentioned inside 'with' scope

### In below example - release will throw exception since its wrapped in  {{- with .Values.favorite }}. We can access it via setting variables.

```
 {{- with .Values.favorite }}
  drink: {{ .drink | default "tea" | quote }}
  food: {{ .food | upper | quote }}
  release: {{ .Release.Name }}
  {{- end }}
```

## range

- Support for looping

```
{{- range .Values.pizzaToppings }}
    - {{ . | title | quote}}
    {{- end}}
```

```
{{- range $key, $val := .Values.json }}
  {{ $key | quote | indent 6}}: {{ $val | quote }}
  {{- end}}
```

```
json:
  key1: val1
  key2: val2
  key3: val3
```