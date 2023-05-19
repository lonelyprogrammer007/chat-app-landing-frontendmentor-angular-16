# Atomic design

# Atoms & Molecules — Dumb components

They are simple, reusable, and easy to test pieces of code. They both receive `@Input` and can emit `@Output`. The perfect candidates for UI libraries.

**Atoms**: The smallest unit possible, reused all over the place. Normally a single HTML element with basic styling.

**Molecules**: A single group of atoms.

## Organisms & Templates — Simplifying smart components

In terms of reducing smart component complexity, templates help reduce the HTML boilerplate, and organisms their TypeScript counterpart.

In my experience leading projects, I found that while these two are keys for app scalability and team performance, they are also rarely seen.

And this is due to temporality. When we initially design a complex smart component, we do it as a whole. We create the full page by slowly adding small chunks. And all of a sudden, a smart component can easily grow up to 500 lines of TypeScript and close to 1K of HTML-CSS, becoming a mud pool where every step is harder to take than the previous one. Even if the logic is simple, the length of the file makes it hard to maintain.

Templates and organisms can help reduce the noise and keep the code structured and ready to scale. It will be easier to recognize and reuse the pieces of code in future similar-looking features.

### Templates

Think of templates as scaffolds & skins for a certain component. Just plain HTML-CSS with `ng-content`.

They are used by higher-order components (like pages or organisms) to take care of style variability and HTML boilerplate. This component shouldn't have any input, output, logic, or constructor dependencies.

Let's see this with a simple example:

FIXME:
![Example](https://miro.medium.com/v2/resize:fit:640/format:webp/1*RRtb7rE8nC1XpA-13RaEwQ.png)

This approach is not only great for small pieces of code, like the Angular Material cards, but also for screen-wide designs. When a layout component with a `router-outlet` isn't enough, or you need to split up the code, this may be a good solution. Once the original code is stable, refactoring to templates is a matter of cut & paste, taking no longer than several minutes.

### Organisms

Group of molecules that act as a unit, with a certain level of complexity. Brad's site uses the header of the page as an example organism.

In my opinion, this is more functional than a structural approach. I like to think of them as widgets. Stand-alone sections of the app that may be reused among multiple pages and have self-contained meaning.

**Are they smart or dumb?**

There is no rule of thumb. I prefer to keep the service dependencies and logic in the page/controller whenever possible. But in reality, for complex pages, it may be recommendable to turn the page into a more layout type and split the logic into several child organism components with their own dependencies.

## Pages — Smart components

Commonly referred to as features in the classic core/features/shared project structure. Smart components manage input/output, connecting with the core of your app via services.

---

Did you find the article interesting? What is your opinion?

As always, thanks for reading! 🙂
