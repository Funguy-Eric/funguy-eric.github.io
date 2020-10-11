# BootStrap

* In order for Bootstrap based site to run normally, following meta is required:

  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```

## Grid System

* official definition for grid system:

  > Bootstrap includes a responsive, mobile device first, unfixed grid system, which can be appropriately expanded to 12 columns with the increase of device or view size. It contains predefined classes for simple layout options, as well as powerful hybrid classes for generating more semantic layouts.

```html
<!-- make sure center and max width-->
<div class="container">
    <!-- each row required class 'row'-->
    <div class="row">
        <!-- "col-md-4" represent a column that takes up 4 cells, 'md' means middle-size devices-->
        <!-- when using on a large device, system will find class with'lg', otherwise with'md'-->
        <div class="col-md-4 col-lg-2"></div>
        <div class="col-md-6 col-lg-8"></div>
        <div class="col-md-2 col-lg-2"></div>
        <!-- all cells in a row cannot add up to more than 12-->
    </div>
</div>

<!-- notice: for small devices like mobile phone, there is also class as 'col-sm-x'
```

* `.clearfix`

  This class can help fix the problem that when using a small device, grid's position cannot be certain.



## Support tag

```html
<div id="text-style">
            <p class="text-left">text-align-left</p>
            <p class="text-center">text-align-center</p>
            <p class="text-right">text-align-right</p>
            <p class="text-muted">muted content</p>
            <p class="text-primary">content with primary class</p>
            <p class="text-success">content with success class</p>
            <p class="text-info">content with info class</p>
            <p class="text-warning">content with warning class</p>
            <p class="text-danger">content with danger class</p>
        </div>

        <div id="header-releated">
            <!-- small stands for inline subtitle -->
            <h1>title h1. <small>subtitle h1</small></h1>
            <!-- class='lead' stands for a paragraph emphasis -->
            <h2>Emphasize a paragraph</h2>
            <p class="lead">This is a emphasized paragraph</p>
            <br>
            <p style="font-size: 30px;" >This section has a<strong> bold part</strong>,<small>a 85% size part</small> and <em>an italic part.</em></em></small></p>
        </div>

        <div id="address-quote">
            <!-- address label create a section for address infomation -->
            <address>
                <strong>Company name, Inc.</strong><br>
                street<br>
                City, State XXXXX<br>
                <abbr title="Phone">P:</abbr> (123) 456-7890
            </address>
            <address>
                <strong>Full Name</strong><br>
                <a href="#">xxxx@xxx.com</a>
            </address>

            <blockquote>
                this is an area for quote
            </blockquote>
```

![](C:\Users\Leonard\Desktop\one.png)

```html
            <!-- class='pull-right' make align right -->
            <blockquote class="pull-right">
                Quote with a sub title that is align right
                <small>a subtitle with <cite title="this is a cite">a cite</cite></cite></small>
            </blockquote>
        </div>

        <div id="list">
            <h3>Definition list</h3>
            <dl>
                <dt>Description 1</dt>
                <dd>Item 1</dd>
                <dt>Description 2</dt>
                <dd>Item 2</dd>
            </dl>

            <h3>Horizontal definition list</h3>
            <!-- Attention: class='dl-horizontal' only works when width of screen is over 768px -->
            <dl class="dl-horizontal">
                <dt>Description 1</dt>
                <dd>Item 1</dd>
                <dt>Description 2</dt>
                <dd>Item 2</dd>
            </dl>

            <h3>Inline list</h3>
            <ul class="list-inline">
                <li>line</li>
                <li>line</li>
                <li>line</li>
                <li>line</li>
            </ul>

            <h3>List with no style</h3>
            <ul class="list-unstyled">
                <li>line</li>
                <li>line</li>
                <li>line</li>
                <li>line</li>
            </ul>
        </div>

        <div id="code">
            <p><code>&lt;span&gt;</code> is an inline code part</p>
            <!-- pre is a code section -->
            <!-- class="pre-scrollable" adds a scroll bar-->
            <pre class="pre-scrollable">
                &lt;article&gt;
                &lt;h1&gt;Article Heading&lt;/h1&gt;
                &lt;/article&gt;
                &lt;span&gt;Hello&lt;/span&gt;
            </pre>
        </div>
```

![](C:\Users\Leonard\Desktop\two.png)