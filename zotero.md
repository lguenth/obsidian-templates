---
tags: {% if itemType == "book" %}
    - book{% else %}
    - paper{% endif %}
title: "{% if creators -%}{{creators[0].lastName}}
        {%- if creators|length == 2 %} & {{creators[1].lastName}}{% endif -%}
        {%- if creators|length > 2 %} et al.{% endif -%}
        {%- endif -%}
        {%- if date %} ({{date | format("YYYY")}}){% endif -%}
        {%- if shortTitle %} {{shortTitle | nl2br}} {%- else %} {{title | nl2br}}
        {%- endif -%}"
projekte: {% for tag in  tags %}{% if "📓" in tag.tag %}
    - "[[{{tag.tag | replace("📓 ", "")}}]]"{% endif %}{% endfor %}
created: {{importDate|format("YYYY-MM-DD")}}
modified: {{importDate|format("YYYY-MM-DD")}}
---
{#- METADATA AND PERMANENT INDEX -#}
{#-  This part only gets inserted once -#}
{#-  You can use this space to take permanent notes, e.g. to create an index or write a summary, or link to other notes #}
{% persist "notes" %}{% if isFirstImport %}

# {{title}}

## 📇 Index
- 

> [!info]+ Metadata – {% for attachment in attachments | filterby("path", "endswith", ".pdf") %}[PDF{% if not loop.first %} {{loop.index}}{% endif %}]({{attachment.desktopURI|replace("/select/", "/open-pdf/")}}){% if not loop.last %}, {% endif %}{% endfor %}
> {{bibliography}}
> 
> - Keywords: 
> - Zotero: [Eintrag öffnen]({{select}}){% if relations %}
> - Related: {% for relation in relations %}{% if relation.citekey %}[[@{{relation.citekey}}]]{% if not loop.last %}, {% endif %}{% endif %}{% endfor %}{% endif %}

> [!example]- Abstract
> *{{abstractNote | nl2br}}*
 
> [!important]- Summary
> 
> {% endif %}{% endpersist %}

{#- WARNING: Everything below this line will get overwritten on re-import! -#}
{#- COLOR VARIABLES -#}
{%-
    set zoteroColors = {
        "#2ea8e5": "blue",
        "#5fb236": "green",
        "#a28ae5": "purple",
        "#ffd400": "yellow",
        "#ff6666": "red",
        "#f19837": "orange",
        "#e56eee": "magenta",
        "#aaaaaa": "grey"
    }
-%}

{%-
   set colorHeading = {
        "blue": "⭐ Main",
        "green": "✅ Definition",
        "purple": "🧩 Methodology",
        "yellow": "📚 Further Reading",
        "red": "⭕ Questions",
        "magenta": "📎 Info",
        "other": "Misc"
   }
-%}

{#- ANNOTATION TYPES -#}
{%- macro calloutHeader(type) -%}
    {%- switch type -%}
        {%- case "highlight" -%}
        Highlight
        {%- case "image" -%}
        Image
        {%- default -%}
        Note
    {%- endswitch -%}
{%- endmacro %}

{#- SET CUSTOM ANNOTATION COLORS -#}
{%- set newAnnot = [] -%}
{%- set newAnnotations = [] -%}
{%- set annotations = annotations | filterby("date", "dateafter", lastImportDate) %}

{% if annotations.length > 0 %}*Imported: {{importDate | format("YYYY-MM-DD HH:mm")}}*

{%- for annot in annotations -%}

    {%- if annot.color in zoteroColors -%}
        {%- set customColor = zoteroColors[annot.color] -%}
    {%- elif annot.colorCategory|lower in colorHeading -%}
    	{%- set customColor = annot.colorCategory|lower -%}
    {%- else -%}
	    {%- set customColor = "other" -%}
    {%- endif -%}

    {%- set newAnnotations = (newAnnotations.push({"annotation": annot, "customColor": customColor}), newAnnotations) -%}

{%- endfor -%}

{#- INSERT ANNOTATIONS -#}
{#- Loops through each of the available colors and only inserts matching annotations -#}
{#- This is a workaround for inserting categories in a predefined order (instead of using groupby & the order in which they appear in the PDF) -#}

{%- for color, heading in colorHeading -%}
{%- for entry in newAnnotations | filterby ("customColor", "startswith", color) -%}
{%- set annot = entry.annotation -%}

{%- if entry and loop.first %}

### {{colorHeading[color]}}
{%- endif %}

> [!quote{{"|" + color if color != "other"}}]+ {{calloutHeader(annot.type)}} ([p. {{annot.pageLabel}}](zotero://open-pdf/library/items/{{annot.attachment.itemKey}}?page={{annot.pageLabel}}&annotation={{annot.id}}))

{%- if annot.annotatedText %}
> {% if annot.hashTags %}[[{{annot.hashTags|replace("#", "")}}]]: {% endif -%}
{{annot.annotatedText|nl2br}}
{%- endif %}

{%- if annot.imageRelativePath %}
> ![[{{annot.imageRelativePath}}]]
{%- endif %}

{%- if annot.ocrText %}
> {{annot.ocrText}}
{%- endif %}

{%- if annot.comment %}
> → **{{annot.comment|nl2br}}**
{%- endif -%}

{%- endfor -%}
{%- endfor -%}
{% endif -%}
