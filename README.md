# jekyll-template
Template for Blog based on jekyll

# How-to
* Base Config: `_config.yml`

  ```
  title: your title
  email: your email
  description: >
    your description
  baseurl: "/jekyll-template" # the subpath of your site, e.g. /blog
  url: "https://zhoukekestar.github.io" # the base hostname & protocol for your site
  twitter_username: zhoukekestar
  github_username:  zhoukekestar

  # paging
  paginate: 10
  paginate_path: "/page:num/"

  # Build settings
  markdown: kramdown
  theme: minima
  kramdown:
  input: GFM
  ```

* Your blog header: `_includes/header.html`

  ```html
     <!-- your blog header -->
    <div class="trigger">
      <a class="page-link" href="/jekyll-template/search">Search</a>
      <a class="page-link" href="/jekyll-template/tags.html">Tags</a>
    </div>
  ```

* Your post comments: `_layouts/post.html`

  ```js
    // fetch your own comments
    fetch('https://api.github.com/repos/zhoukekestar/jekyll-template/issues/{{page.commentIssueId}}/comments', {
      headers: {
        Accept: "application/vnd.github.full+json"
      }
    }).then(function (response) {
      return response.json();
    }).then(function (body) {
      loadComments(body);
    })
  ```

* Your custom style: `css/main.scss`

  ```css
    .abc {
    /* your custom style */
    }
  ```
