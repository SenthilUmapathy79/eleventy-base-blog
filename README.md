# eleventy-base-blog

A starter repository showing how to build a blog with the [Eleventy](https://github.com/11ty/eleventy) static site generator.

## Getting Started

### 1. Clone this repository:

```
git clone https://github.com/11ty/eleventy-base-blog.git my-blog-name
```


### 2. Navigate to the directory

```
cd my-blog-name
```

Specifically have a look at `.eleventy.js` to see if you want to configure any Eleventy options differently.

### 3. Install dependencies

```
npm install
```

### 4. Run Eleventy

```
npx eleventy
```

Or build automatically when a template changes:
```
npx eleventy --watch
```

Or in debug mode:
```
DEBUG=* npx eleventy
```

### Implementation Notes

* `posts/` has the blog posts but really they can live in any directory. They need only the `post` tag to be added to this collection.
* Add the `nav` tag to add a template to the top level site navigation. For example, this is in use on `index.njk` and `about/index.md`.
* `about/index.md` shows how to add a content page.
* Content can be any template format (blog posts needn’t be markdown, for example). Configure your supported templates in `.eleventy.js` -> `templateFormats`.
* Because `css` and `png` are listed in `templateFormats` but are not supported template types, any files with these extensions will be copied without modification to the output (while keeping the same directory structure).
* The blog post feed template is in `feed/feed.njk`. This is also a good example of using a global data files in that it uses `_data/metadata.json`.
* This example uses three layouts:
  * `_includes/layouts/base.njk`: the top level HTML structure
  * `_includes/layouts/home.njk`: the home page template (wrapped into `base.njk`)
  * `_includes/layouts/post.njk`: the blog post template (wrapped into `base.njk`)
* `_includes/postlist.njk` is a Nunjucks macro and is used to display a list of all the posts. Use it like this:
```
{% import "postlist.njk" as postsm %}
{{ postsm.list(collections.post, page) }}
```
