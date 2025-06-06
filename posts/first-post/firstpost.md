<div class="yaml-meta">
Title: First Post<br>
Date: 2025-06-07<br>
Category: First Post<br>
Tags: blogging, latex, language-learning, html coding<br>
</div>

## First Post - underscore and \<em\>

I have thought about many possible topics for the first post of this time capsule series, or simply, my blog. Some notes in physics, perhaps? I was considering a summary of fluid equations frequently used in stellar physics, maybe even a discussion of Eulerian and Lagrangian perturbations in fluids involving Lie derivatives. Or I could have written about how I envision myself throughout my PhD journey at UVA.

But no - I ended up deciding to write about how I spent an entire afternoon just getting this blog to function properly. Despite it being random, it marks the beginning of a series (will it really become one?). So I think it deserves a place here. Given the reverse chronological order of the time capsule page, if I keep posting(hopefully), this post will eventually be pushed to the very last page. In the end, readers will find their way to the other posts anyway.

## What happened (it's short actually)

I was using an AI-generated Markdown file to test embedding it into ab HTML page. (for the template file please visit [here](/posts/template))

I was expecting it to be simple and quick, the internet says there are Mathjax and KaTeX packages, for rendering $\text{\LaTeX}$ expressions. After following the tutorial of Mathjax, only a $1/4$ of the equation were rendered. With some slight fix I made a part of the inline math rendered. I then used copilot and other tools, to try to display the remaining expressions, but failed. I was questioning myself about whether it's the CSS issue, but a blank html file without style setting wouldn't work wither. Maybe writing the html all by myself isn't a good idea...

So - I went to [https://gohugo.io/](https://gohugo.io/), which offers some good templates, and the hugo system automatically compiles the markdown file into html. The equations failed to render all had either \<em\> or \</em\> at where it should be an underscore..

I wasn't outputing the transcribed code directly so I wasn't able to notice the extra \<em\>. (though I should have as part of the unrendered text is slanted).
```
fetch('./template.md')
            .then(response => response.text())
            .then(text => {
                let html = marked.parse(text);

                document.getElementById('markdown-content').innerHTML = html;
                renderMathInElement(document.getElementById('markdown-content'), {
                delimiters: [
                    { left: "$$", right: "$$", display: true },
                    { left: "$", right: "$", display: false }
                ]
                });
            });
```

By adding the line below to the fetch module, the problem is solved and I don't need to use other people's templates finally...

```
// Replace <em> and </em> with _ only inside math blocks
// This is a simple but effective approach for most cases:
html = html.replace(/<em>/g, '_').replace(/<\/em>/g, '_');
```

## About blog posts

I think (at least for now) I will continue doing this thing. I feel both my English and Chinese are getting rusty, and I hope writing and reading more will help. Language studies is also a good topic to write about, in my opinion. I am in the progress of learning japanese. I am able to converse but still can't fully express what I think, so win an argument in japanese is rather impossible for now. But I will see if I can pick any interesting topics to write about in the future.

I plan to take JLPT N1 exam at the end of this year, so wish me good luck.. After passing the N1 exam (hopefully this December), I plan to keep refining my Japanese with 八木さん - my super nice advisor, and start learning Flemish - the Dutch language spoken in Belgium, hopefully there will be enough resource for it.

![My Ridley Flandrien Bike](./bike.jpg "My Ridley Flandrien Bike")