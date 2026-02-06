---
permalink:  index.html
layout:     page
nav-name:   home
---

# Pavel's Homepage

Hi I'm Pavel Hájek from Prague, Czech Republic, and this is my personal website.
I studied mathematics and physics and have worked as a mathematician, software engineer, and computational researcher at the Wolfram Institute.
Find more in the respective categories.

* **[Math](Math.html)**
* **[Software](Software.html)**
* **[Wolfram](Wolfram.html)**
* **[Hobbies](Hobbies.html)**

From time to time I also drop a blog post.

* **[Posts](Posts.html)**

## Contact

Please contact me via the contact form.

{% include contact-form.html %}

[PGP]:{{ site.url }}/assets/pgpkey.asc

Here is my [PGP key][PGP].

## Recent Posts

<div class="posts">
      <table style="table-layout:fixed;" cellspacing=0 cellpadding=0>
      {%- for post in site.posts limit:5 %}
      <tr>
        <td style="white-space: nowrap; vertical-align: top; padding-right: .3em">
           {{ post.date | date: "[%b %d, %Y]" }}
        </td>
        <td>
          <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title }}
          </a>
        </td>
      </tr>
      {%- endfor -%}
    </table>
</div>
