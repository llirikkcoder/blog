<!--
{
  "layout": "article",
  "title": "How Web Components Will Change CSS Best Practices",
  "date": "2014-10-31T22:01:36-07:00",
  "draft": true,
  "tags": [
    "CSS",
    "HTML",
    "JavaScript"
  ]
}
-->

For about as long as people have been writing CSS, people have been writing CSS the same way. Our tools change, methodologies go in an out of fashion, but at the end of the day, most of us serve one CSS file that styles our entire site.

This isn't a critique of our current best-practices, it simply the reality. When we say we write modular CSS we mean that nominally. All CSS rules are global and every rule has the potential to conflict with every other rule. This is just the way it is.

People who are new to CSS often complain that things which should be simple are unnecessarily complex, unintuitive, or hacky. Why do I have to use `border-color: transparent` to make a triangle? Why doesn't `vertical-align: center` ever work when I want it to? Why are the position keywords `static`, `absolute`, and `fixed` all sound like they do the same thing?

Sure these are annoyances, and yes being skilled at CSS does require an encyclopedic knowledge of hacks and tricks, but these things are not the truly hard problems of CSS. These are not the problems that make it nearly impossible to redesign without starting over or prevent the development of new features for fear of the consequences of changing *anything*!

The longer I work in this industry, the more I'm convinced that there are really just two hard problems in CSS:

1. Getting your rules to match the elements you want without them accidentally matching the elements you don't.
2. Solving the first problem without writing too much code.

While this might seem like an oversimplification, I believe it's true. Every truly hard problem I've ever faced in CSS has involved fighting with an existing stylesheet. Far too often this is my dilemma:

* I can't write the rules I want because the existing rules trump them.
* I can't change the existing rules because refactoring would take too long.
* My hand is forced, and I end up writing rules I know are bad.
* Now the problem is worse than when I started.

The situation exists because developers routinely come up with bad solutions to hard problem #2. They think they're being clever, but they're really just digging a whole they'll eventually fall into.

Developers like to notice patterns, and they've been taught not to repeat themselves. So when a developer looks at a site and notices that every time an `<h3>` is followed by `<ul>` in the sidebar, there's a 20px gap, what do you expect him to do? Most people who encounter this scenario write some form of the following rule:

```css
#sidebar h3 + ul {
  margin-top: 20px;
}
```
