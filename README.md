<h1>CodeIgniter Sitemap Generator Model</h1>

Generate a sitemap or sitemap index file for your web application with the CodeIgniter PHP framework.
This CodeIgniter model quickly enables you to generate a valid SEO-friendly sitemap file for you web application and/or website. An XML sitemap file helps crawlers of search engines to easily navigate and browse through your website and understand the structure of the different urls.

<h2>What are sitemaps?</h2>
Sitemaps are an easy way for webmasters to inform search engines about pages on their sites that are available for crawling. In its simplest form, a Sitemap is an XML file that lists URLs for a site along with additional metadata about each URL (when it was last updated, how often it usually changes, and how important it is, relative to other URLs in the site) so that search engines can more intelligently crawl the site.

Web crawlers usually discover pages from links within the site and from other sites. Sitemaps supplement this data to allow crawlers that support Sitemaps to pick up all URLs in the Sitemap and learn about those URLs using the associated metadata. Using the Sitemap protocol does not guarantee that web pages are included in search engines, but provides hints for web crawlers to do a better job of crawling your site.

<a href="http://www.sitemaps.org/protocol.html" title="Read more about the Sitemap protocol">Read more about the Sitemap protocol on sitemaps.org</a>.

<h2>Usage</h2>

The model is designed to be called and controlled by a CodeIgniter controller. The model does not create and save an actual XML-file to be saved on the disk. Rather, it generates a valid XML-file upon each request and directly serves it to the controller and thus the client browser.

This means that two examples of sitemap files to submit to search engines could look like the following urls:

```
http://www.example.com/index.php/sitemap/general
http://www.example.com/index.php/sitemap/articles
```

<h3>Load the model</h3>
You can load the sitemap model from your CodeIgniter controller with the following line of code:

```HTML+PHP
$this->load->model('sitemapmodel');
```

<h3>Add an item</h3>
To add an item to the sitemap, use the following line of code:

```HTML+PHP
$this->sitemapmodel->add('http://www.example.com/contact', '2015-11-02', 'monthly', 0.9);
```

This function checks for the validity of the item on two points:

<ol>
<li>The value of the parameter <b>changefreq</b> must be one of the following options:
<ul>
<li>always</li>
<li>hourly</li>
<li>daily</li>
<li>weekly</li>
<li>monthly</li>
<li>yearly</li>
<li>never</li>
</ul>
</li>
<li>The value of the parameter <b>priority</b> must be a value between 0 and 1</li>
</ol>

If any of the checks fail, an error is triggered by the model.

<h3>Generate a sitemap file</h3>
When you have inserted all the items in the sitemap, you can call the SEO-friendly valid XML-code by calling a simple line of code:

```HTML+PHP
$this->sitemapmodel->output();
```

<h3>Generate a sitemap index file</h3>
A sitemap index file is a sitemap pointing to one or more other sitemap files. This helps search engine crawlers to easily understand the diversity of sitemaps that are served by your website. To call a sitemap index file instead of a regular sitemap file, simply add the string 'sitemapindex' as a parameter to the output-function, like this:

```HTML+PHP
$this->sitemapmodel->output('sitemapindex');
```

<h3>Clear the sitemap</h3>
If you wish to clear the items in the sitemap, call the following function:

```HTML+PHP
$this->sitemapmodel->clear();
```

