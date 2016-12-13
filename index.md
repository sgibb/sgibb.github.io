---
layout: page
title: Sebastian Gibb
redirect_from:
    - research.html
---

<img class="photo" alt="photo of sebastian" src="https://www.gravatar.com/avatar/6e612cc57c8fc7e840191ce767a0ea46?s=150&amp;d=identicon" />

I am a medical doctor working as a resident at the [Department of Anaesthesiology and Intensive Care of the University Medicine Greifswald](http://www2.medizin.uni-greifswald.de/intensiv/).

In 2010 I joined the [Statistics and Computational Biology research group](http://strimmerlab.org)
headed by [Korbinian Strimmer](http://strimmerlab.org/korbinian.html) and worked on computational proteomics,
namely the analysis of MALDI-TOF mass spectrometry data. In this time I developed [MALDIquant](http://strimmerlab.org/software/maldiquant/) and friends.

You could write me an <a href="mailto:{{ site.email }}">e-mail</a> or find me on:
{% for entry in site.data.social %} [{{ entry.title}}]({{ entry.url }}){% unless forloop.last %}, {% endunless %}{% endfor %}.

<div class="clear"> </div>

{% for cv in site.data.cv %}
## {{ cv.type }}
{% for entry in cv.entries %}
- **{{ entry.time }}**: {{ entry.title }}
{% endfor %}
{% endfor %}

## Software
{% for software in site.data.software %}
### {{ software.type }}
{% for entry in software.entries %}
- [{{ entry.name }}]({% if entry.bioc %}http://bioconductor.org{% else %}http://cran.r-project.org/web{% endif %}/packages/{{ entry.name }}/):
  {{ entry.description }}.
  [[github](https://github.com/{% if entry.github %}{{ entry.github }}{% else %}{{ entry.name | prepend: "sgibb/" }}{% endif %}){% if entry.url %}, [website]({{ entry.url }}){% endif %}]
{% endfor %}
{% endfor %}

## Publications
{% for pubs in site.data.publications %}
### {{ pubs.name }}
{% for entry in pubs.entries %}
- **{{ entry.title }}**.<br />
  {{ entry.authors | replace:'S. Gibb','*S. Gibb*' }}. {{ entry.year}}.<br />
  {% if entry.journal %}{{ entry.journal }}.<br />{% endif %}{% if entry.doi %}DOI: [{{ entry.doi}}](https://doi.org/{{entry.doi}}).{% endif %} {% if entry.arxiv %} arXiv: [{{ entry.arxiv }}](https://arxiv.org/abs/{{entry.arxiv }}).{% endif %}{% if entry.misc %}{{ entry.misc }}.{% endif %}
{% endfor %}
{% if pubs.name == "Publications" %}
(&sup1; equal contributors)
{% endif %}
{% endfor %}


### Recent presentations
{% for entry in site.data.talks limit: 2 %}
- **{{ entry.title }}**.<br />
  {{ entry.date }}. {{ entry.location }}. [[pdf]({{ entry.url }})].<br />
{% endfor %}

## Contact

<address>
<table><tbody>
    <tr>
        <td class="col1">name:</td>
        <td class="col2">Sebastian Gibb</td>
    </tr>
    <tr>
        <td class="col1">address:</td>
        <td class="col2">Peter-Warschow-Stra&szlig;e 52<br>D-17489 Greifswald</td>
    </tr>
    <tr>
        <td class="col1">e-mail:</td>
        <td class="col2"><a href="mailto:{{ site.email}}">{{ site.email }}</a></td>
    </tr>
</tbody></table>
</address>

