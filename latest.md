---
layout : topic
title : Latest
---

## <a name="version"></a>Version

The current version of Sempiler is **0.1**.

## <a name="distros"></a>Distros

Sempiler is currently available in the following formats:

<ul class="media-list">
    <li>
        <a class="lozenge" href="https://marketplace.visualstudio.com/search?term=sempiler&amp;target=VSCode&amp;category=All%20categories&amp;sortBy=Relevance">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/vsc-logo2.png" alt="visual studio code logo"/>
        </a>

        <a href="{{ site.baseurl }}/{{ site.github.repository_name }}/features/vsc-ext">docs</a>
    </li>
</ul>

{% include divider.html %}

## <a name="sources"></a>Sources

Sempiler currently supports the following languages as **source code input**:

### <a name="typescript"></a>TypeScript

<ul class='feature-meta lozenge left-align bottom-gutter'>
    <li>version <strong>vNext</strong></li>
</ul>

TypeScript is a suitable source language for the project given it's **expressive, modern syntax and well defined type system**. 

It is accessible to native programmers, and an easy transition syntactically for the many web developers who currently use JavaScript as their primary programming language.

## <a name="targets"></a>Targets

Sempiler currently supports the following targets for **native code emission**:

### <a name="c++"></a>C++
<ul class='feature-meta lozenge left-align bottom-gutter'>
    <li>version <strong>vNext</strong></li>
</ul>

C++ is still incredibly popular and will continue to be given it's role as the de facto language of choice for the AAA game industry and CPU intensive projects like TensorFlow.

By targeting C++ we can write **truly native desktop apps** on platforms like Windows without needing to host them inside a virtualization layer.

We can even **build WASM web apps** by using emscripten [stub APIs](stub-apis) in TypeScript, and sempiling to C++ 🤖

### <a name="Swift"></a>Swift
<ul class='feature-meta lozenge left-align bottom-gutter'>
    <li>version <strong>vNext</strong></li>
</ul>

Initial Swift support was introduced shortly after [C++](#c++) because it is fundamentally different semantically from the C family of languages, which helped in establishing the validity of the sempiler concept.

Moreover, it allows us to sempile to **truly native mobile apps** from a *web* language without the use of a heavy framework or virtual machine on the client.

### And More to come...


{% include agnostic.html %}

{% include divider.html %}

## <a name="contributing"></a>Contributing

The project is in the early stages so we thank you for your patience, and greatly appreciate your interest. 

### <a name="issues-and-requests"></a>Issues & Requests

**Bug reports and feature requests** can be submitted on the {% include external-link.html link=site.github.repository_url label="Github repository" %}. 

**General questions and comments** can be submitted via {% include external-link.html link=layout.twitterUrl label="Twitter" %}.

If the problem is missing support for a language construct please submit this as a **feature request rather than a bug**.


In either case please include the following (where applicable):
- Clear description
- Steps to reproduce
- Example source code
- Environment specs

This information will be conducive to a focused and efficient discussion.

Please always be **respectful to other community members** - no matter how frustrating a bug or missing feature is!

### <a name="stub-apis"></a>Stub APIs

If you would like to write [stub APIs](stub-apis) for core symbols or popular libraries on target platforms that would be awesome! 

For now please submit them as a [feature request](#issues-and-requests) for us to include them on `master`. 

### <a name="new-languages"></a>New Languages

Extending both the source and target languages is an ongoing goal for the Sempiler project, and each one added helps **validate the idea of semantic transpilation**.

For now please submit a new language [feature request](#issues-and-requests) to get a dialog going.


{% include divider.html %}

## <a name="team"></a>Team

<ul class="media-list">
    <li>
        <a class="lozenge" href="{{ layout.twitterUrl }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/dho.png" alt="d ho"/>
        </a>

        <a href="{{ layout.twitterUrl }}" target="_blank">D Ho</a>
    </li>
</ul>


## <a name="more"></a>More



<ul class="media-list">
    <li>
        <a class="lozenge" href="{{ site.github.repository_url }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/github-logo2.png" alt="github logo"/>
        </a>

        <a href="{{ site.github.repository_url }}" target="_blank">Github</a>
    </li>    
    
    <li>
        <a class="lozenge" href="{{ layout.visualStudioUrl }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/vsc-logo2.png" alt="visual studio code logo"/>
        </a>

        <a href="{{ layout.visualStudioUrl }}" target="_blank">Code</a>
    </li>


    <li>
        <a class="lozenge" href="{{ layout.youtubeUrl }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/yt-logo.png" alt="youtube logo"/>
        </a>

        <a href="{{ layout.youtubeUrl }}" target="_blank">YouTube</a>
    </li>

    <li>
        <a class="lozenge" href="{{ layout.facebookUrl }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/fb-logo.png" alt="facebook logo"/>
        </a>

        <a href="{{ layout.facebookUrl }}" target="_blank">Facebook</a>
    </li>
    
    
    <li>
        <a class="lozenge" href="{{ layout.twitterUrl }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/twitter-logo.png" alt="twitter logo"/>
        </a>

        <a href="{{ layout.twitterUrl }}" target="_blank">Twitter</a>
    </li>

    <li>
        <a class="lozenge" href="{{ layout.patreonUrl }}" target="_blank">
            <img src="{{ site.baseurl }}/{{ site.github.repository_name }}/images/patreon-logo.png" alt="patreon logo"/>
        </a>

        <a href="{{ layout.patreonUrl }}" target="_blank">Patreon</a>
    </li>
</ul>