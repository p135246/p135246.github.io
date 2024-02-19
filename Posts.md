---
layout:     page
nav-name:   posts
---
# Posts (All)

<div class="posts">
      <table style="table-layout:fixed;" cellspacing=0 cellpadding=0>
      {%- for post in site.posts %}
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
