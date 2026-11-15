---
permalink:  index.html
layout:     page
nav-name:   home
---

# Pavel's Homepage

Hi, I'm Pavel Hájek from Prague, Czech Republic, and this is my personal website.
I studied mathematics and physics and have worked as a mathematician, software engineer, and computational researcher at the Wolfram Institute.

<div class="home-actions">
  <a class="home-work-link" href="WorkWithMe.html">
    <span aria-hidden="true">🤑</span>
    Work with me
  </a>
  <a class="home-coffee-link" id="support" href="https://buymeacoffee.com/pavel_hajek" target="_blank" rel="noopener">
    <span aria-hidden="true">☕</span>
    Buy me a coffee
  </a>
</div>

I’m also on [GitHub][github], [ORCID][orcid], and [Wolfram Community][wolfram-community].
I’m part of the [MultiHistory][multihistory] and [Arity Science][arity-science] research collaborations.
On YouTube, see [Multihistory Science][multihistory-youtube] and [EigenAudio][eigenaudio].

For more details, browse by category in the menu above or see all [Posts](Posts.html) at once.

Use the [contact form][contact] to get in touch.
{: #contact }

Also check out my wife's [photography website](https://www.tunievaphotography.com).

{% assign recent_posts = site.posts | where_exp: "post", "post.pinned != true" %}
{% include post-index.html posts=recent_posts heading="Recent Posts" limit=5 %}

{% assign pinned_posts = site.posts | where: "pinned", true %}
{% include post-index.html posts=pinned_posts heading="Pinned Posts" %}

[contact]: /Contact.html
[multihistory]: https://multihistory.org/
[arity-science]: https://arity.science/
[github]: https://github.com/p135246
[orcid]: https://orcid.org/0009-0001-7406-0028
[wolfram-community]: https://community.wolfram.com/web/hajekpavel
[eigenaudio]: https://www.youtube.com/@EigenAudio
[multihistory-youtube]: https://www.youtube.com/@MultiHistoryScience
