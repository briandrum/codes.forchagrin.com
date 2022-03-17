---
layout: home
---

{% assign sortedParts = site.data.parts | sort: "number" %}

{% for part in sortedParts %}

  <details>
    <summary>Part {{ part.number_word }}: {{ part.name }}</summary>
    {% if part.titles %}
      {% assign sortedTitles = part.titles | sort: "number" %}      
      {% for title in sortedTitles %}
        <p><strong>Title {{ title.number_word }}: {{ title.name }}</strong></p>
        {% assign sortedPages = site.pages | sort: "chapter_no" %}
        <ul>
          {% for page in sortedPages %}
            {% if page.part_no == part.number and page.title_no == title.number %}
              <li><a href="{{ page.url | relative_url  }}">{{ page.title }}</a></li>
            {% endif %}
          {% endfor %}
        </ul>
      {% endfor %}
    {% else %}
      <ul>
        {% assign sortedPages = site.pages | sort: "chapter_no" %}
        {% for page in sortedPages %}
          {% if page.part_no == part.number %}
            <li><a href="{{ page.url | relative_url  }}">{{ page.title }}</a></li>
          {% endif %}
        {% endfor %}
      </ul>
    {% endif %}
  </details>
{% endfor %}

## Disclaimer

The Codified Ordinances and other documents that appear in this repository may
not reflect the most current legislation adopted by the Municipality. The
Codified Ordinances are provided for informational purposes only and should not
be relied upon as the definitive authority for local legislation. Additionally,
the formatting and pagination of the posted documents vary from the formatting
and pagination of the official copy. The official printed copy of the Codified
Ordinances should be consulted prior to any action being taken.

For further information regarding the official version of any portion of the
Codified Ordinances in this repository, please contact the Municipality
directly.
