# Pelican **Z** Theme

Theme hacked from [Gilsondev](https://github.com/gilsondev/pelican-clean-blog).

Original theme based on [Clean Blog layout](https://github.com/BlackrockDigital/startbootstrap-clean-blog).

>:warning: This theme requires Pelican 4.0.0 or newer.

## Screenshot

![Screenshot](WIP.jpg)

## News and Improvements

### New, more modern font

Changed the original Open Sans font with a more modern, nice, readable *Fira Sans*.

### Site Logo:

> Work in progress...

### Tipue Search

[**Tipue Search**](https://github.com/pelican-plugins/tipue-search) **v7.1** has been integrated into the theme.

TODO: search box & search results styling

### Static Comments Plus

**For ethical/privacy reasons DISQUS comment system has been removed**.

[**Static Comments Plus**](https://github.com/mpaglia0/Static_Comments_Plus) has been hacked from [Static Comments](https://github.com/getpelican/pelican-plugins/tree/master/static_comments) Pelican plugin and has the following improvements:

- Added a ``STATIC_COMMENTS_EXT`` parameter in order to choose if comments have to be written in *Markdown* or *reST* format (default). Work In Progress...

- Added a PHP script that will allow visitors to send comments through a form instead of an email (like Static Comments do).

- Minor aesthetic changes.

### Contact Form:

> Work in progress...

# Basic theme configuration

>:warning: All following configurations are valid only for **Z** theme.

>📑 All properties have to be entered in ``pelicanconf.py``.

For your convenience, you can find a ``pelicanconf.py`` template in this repo. This is a good starting point.

### Header Covers

To define custom header cover, set the property ``HEADER_COVER``:

```python
HEADER_COVER = 'enter/your/path/my_image.png'
```

### Header Color

To define a simple header background color, set the property ``HEADER_COLOR``:

```python
HEADER_COLOR = 'black'
```

you can use any valid css color.

### Social URLs

Github, Twitter and Facebook URLs set these properties:

```python
SOCIAL = (('twitter', 'https://twitter.com/myprofile'),
          ('github', 'https://github.com/myprofile'),
          ('facebook','https://facebook.com/myprofile'),
          ('flickr','https://www.flickr.com/myprofile/'),
```

If you have more links add them to SOCIAL. The Name has to be the name of the corresponding FontAwesome icon.
If ``SHOW_SOCIAL_ON_INDEX_PAGE_HEADER`` is set to ``True`` social icons will be
shown under site sub-title on the index page.

### External feed URL

You can specify an external feed URL (e.g. FeedBurner) in ``SOCIAL`` using the
``rss`` or ``rss-square`` icons. The icon will be shown in the footer with the
rest of your ``SOCIAL`` accounts. A ``<link>`` tag for the external feed will be
placed in ``<head>`` instead of the default Pelican feeds.

### Single author tweak

Pelican has been designed for a multi-author site. Clicking on each author name will redirected the visitor
to a page containing all articles of the clicked author. If you are the unique author of the blog, this behaviour causes a boring
loop because all articles belong only to you...

Set

```python
AUTHOR_URL = ''
AUTHOR_SAVE_AS = ''
AUTHORS_SAVE_AS = ''
```

so single author pages will not been created, and then

```python
SINGLE_AUTHOR_SAVE_AS = 'your-static-presentation-page/index.html'
```

in order to redirect the visitor to a single static page.

### Back-To-Top button

A simple/themeable back-to-top button is available.

Simply set ``BACKTOTOP_BTN`` to ``True`` in order to enable it.

### Code highlights

This theme contains this color schemes:

 - Tomorrow - ``tomorrow.css``;
 - Tomorrow Night - ``tomorrow_night.css``;
 - Monokai - ``monokai.css``;
 - Github - ``github.css``;
 - Github Jekyll (Gray BG Jekyll way) - ``github_jekyll.css``;
 - Darkly (Default) - ``darkly.css``;

To customize, define ``COLOR_SCHEME_CSS`` with css filename.

Example:

```python
COLOR_SCHEME_CSS = 'monokai.css'
```

### User defined CSS

Define ``CSS_OVERRIDE`` to insert a user defined CSS file
after theme CSS. Example:

```python
CSS_OVERRIDE = 'enter/your/path/myblog.css'
```

### Disable theme JavaScript

Set ``DISABLE_CUSTOM_THEME_JAVASCRIPT`` to ``True`` if you want to disable
``js/clean-blog.min.js`` in case it affects forms and input fields.

### User defined footer

Define ``FOOTER_INCLUDE`` to insert a custom footer text
instead of the default "Powered by Pelican". The value is a template path. You also
need to define the ``EXTRA_TEMPLATES_PATHS`` setting. If your custom footer
template is stored under the content ``PATH`` then Pelican will try to render
it as regular HTML page and will most likely fail. To prevent Pelican from
trying to render your custom footer add it to ``IGNORE_FILES``.

Example:

```python
FOOTER_INCLUDE = 'myfooter.html'
IGNORE_FILES = [FOOTER_INCLUDE]
EXTRA_TEMPLATES_PATHS = [os.path.dirname(__file__)]
```

> :warning: Avoid using names which duplicate existing templates from the
theme directory, for example ``footer.html``. Due to how Pelican searches the
template directories it will first find the files in the theme directory and you
will not see the desired results.

### Dynamic Copyright year

Enter a ``COPY_DATE`` value if you need a static Copyright year.

If you need a dynamic Copyright year (i.e. the current year) proceed in this way:

1. At the beginning of your ``pelicanconf.py`` enter the Python function ``from datetime import date``
2. Then set ``DCOPY_DATE`` with value ``date.today().year``. This will return the current year.

You can use the static or the dynamic year or also both, like in the following example:

```python
COPY_DATE = '2015 -'
DCOPY_DATE = date.today().year
```

Will return -> **2015 - 2021**

### Analytics

**Removed Google and Gauges Analytics for ethical/privacy reasons**.

Kept only the free Matomo (aka Piwik) system.

 - Piwik: ``PIWIK_URL`` and ``PIWIK_SITE_ID``.

### Favicon

To define if using a favicon and its format:

```python
FAVICON = 'favicon.ico'
```

> :warning: It is necessary ``STATIC_PATHS`` configured!

```python
STATIC_PATHS = ['images', 'extra/favicon.ico']
EXTRA_PATH_METADATA = {
    'extra/favicon.ico': {'path': 'favicon.ico'}
}
```

### Other configuration parameters

 - If ``ADDTHIS_PUBID`` is defined, sharing buttons from AddThis will appear
 at the bottom of the article;
 - ``GOOGLE_SITE_VERIFICATION`` - Google site verification token;
 - ``BING_SITE_VERIFICATION`` - Bing site verification token;
 - Set ``SHOW_FULL_ARTICLE`` to ``True`` to show full article content on index.html
 instead of summary;
 - Set ``SHOW_SITESUBTITLE_IN_HTML`` to ``True`` to make use of the ``SITESUBTITLE``
 variable inside the ``<title>`` HTML tag;
 - Set ``FACEBOOK_ADMINS`` to a list of Facebook account IDs which are
 associated with this blog. For example ``['12345']``. For more info see
 https://developers.facebook.com/docs/platforminsights/domains

### Translation for templates strings

A gettext method has been used. This is useful if you have only a few strings to be translated.

At the bottom of your ``pelicanconf.py`` file enter the following instruction:

```python
# custom Jinja2 filter for localizing theme
def gettext(string, lang):
    if lang == "en":
        return string
    elif lang == "it":
        if string == "Archives": return "Archivi"
        elif string == "Archives for": return "Archivi per"
	elif string == "Posted by": return "Pubblicato da"
	...
        ...
        else: return string
        
 JINJA_FILTERS = {
     "gettext": gettext,
}
```

### Articles

 - To customize header cover to articles, insert the metadata ``header_cover``.
 - To customize OpenGraph images, insert the metadata ``og_image``, otherwise
 ``header_cover``, ``HEADER_COVER`` or a default image is used.
 - To customize Twitter card images, insert the metadata ``twitter_image``,
 otherwise ``header_cover``, ``HEADER_COVER`` or a default image is used.
 Twitter cards are automatically generated if the ``twitter`` icon is configured
 in ``SOCIAL``!

All image paths are relative from the site root directory!

You can also use absolute URLs for ``og_image`` and ``twitter_image``.

Example:

 - To RST

```rst
My super title
##############

:date: 2010-10-03 10:20
:modified: 2010-10-04 18:40
:tags: thats, awesome
:category: yeah
:slug: my-super-post
:authors: Alexis Metaireau, Conan Doyle
:summary: Short version for index and feeds
:header_cover: /images/posts/super-title/cover.png
:og_image: /images/posts/super-title/facebook_cover.png
:twitter_image: /images/posts/super-title/twitter_cover.png
```

 - To Markdown

```markdown
Title: My super title
Date: 2010-12-03 10:20
Modified: 2010-12-05 19:30
Category: Python
Tags: pelican, publishing
Slug: my-super-post
Authors: Alexis Metaireau, Conan Doyle
Summary: Short version for index and feeds
Header_Cover: /images/posts/super-title/cover.png
Og_Image: http://example.com/facebook_cover.png
Twitter_Image: http://example.com/twitter_cover.png

This is the content of my super blog post.
```

Other metadata can be created to assign resume of article, with ``headline``:

 - To RST

```rst
My super title
##############

:date: 2010-10-03 10:20
:modified: 2010-10-04 18:40
:tags: thats, awesome
:category: yeah
:slug: my-super-post
:authors: Alexis Metaireau, Conan Doyle
:summary: Short version for index and feeds
:headline: Resume of article
```

 - To Markdown

```markdown
Title: My super title
Date: 2010-12-03 10:20
Modified: 2010-12-05 19:30
Category: Python
Tags: pelican, publishing
Slug: my-super-post
Authors: Alexis Metaireau, Conan Doyle
Summary: Short version for index and feeds
Headline: Resume of article

This is the content of my super blog post.
```

Feel free to use **Z** for your projects and send comments and/or suggestions.

Enjoy!
