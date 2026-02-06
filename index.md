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
* **[Posts](Posts.html)**

You can [contact me](#contact) or [support me](#support) below.

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

## <a id="contact"></a>Contact

Please contact me via the contact form or using my [PGP key][PGP].

{% include contact-form.html %}

[PGP]:{{ site.url }}/assets/pgpkey.asc

## <a id="support"></a>Support

<a href="https://buymeacoffee.com/pavel_hajek" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="40">
</a>
