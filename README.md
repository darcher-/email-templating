# modern-email
A modern approach to email templating

**requires use of inliner (e.g. https://putsmail.com/inliner)**

##### To Do
- [x] initial upload of base layout and elements
- [ ] documentation
- [ ] compiled & inlined versions
- [ ] create various themes for template
- [ ] additional element styling
- [ ] additional modules

##### Table of Contents 

* [Modules](#modules)
  * [One Column](#onecol)
  * [Two Columns](#twocol)
    * [Image Columns](#imgcol) 
    * [Alternate Columns](#altcol) 
  * [Three Columns](#threecol)   

---

<a name="modules"/>

### Modules
Majority of your code will be repetative with slight variations, primarily in width's.

<a name="onecol"/>

#### Single column Module

`.col` fits to content, use `.col-fill` to force `100%` width to fill empty whitespace.

```HTML
<table class="module two-col">
  <tr>
    <td class="frame">
      <table class="pane">
        <tr>
          <td class="text-center text-top">
            <!--[if (gte mso 9)|(IE)]><table align="center" bgcolor="#ffffff" border="0" cellpadding="0" cellspacing="0" width="100%"><tr><td align="center" style="font-size:0" valign="top"><![endif]-->
            <div class="col col-fill text-top">
              <table>
                <tr>
                  <td class="content text-left">
                    <div class="p">Column One</div>
                  </td>
                </tr>
              </table>
            </div>
            <!--[if (gte mso 9)|(IE)]></td></tr></table><![endif]-->
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>
```

<a name="twocol"/>

#### Two column modules

* adding a `.two-col` class onto the `.module` wrapper will apply a max-width `.col` class allowing space for 2 columns.
* conditional comments `<td>` gets a `width="50%"` to accomodate Outlook Express engine clients.

```HTML
<table class="module two-col">
  <tr>
    <td class="frame">
      <table class="pane">
        <tr>
          <td class="text-center text-top">
            <!--[if (gte mso 9)|(IE)]><table align="center" bgcolor="#ffffff" border="0" cellpadding="0" cellspacing="0" width="100%"><tr><td align="center" style="font-size:0" valign="top" width="50%"><![endif]-->
            <div class="col col-fill text-top">
              <table>
                <tr>
                  <td class="content text-left">
                    <div class="p">Column one</div>
                  </td>
                </tr>
              </table>
            </div>
            <!--[if (gte mso 9)|(IE)]></td><td align="center" style="font-size:0" valign="top" width="50%"><![endif]-->
            <div class="col col-fill text-top">
              <table>
                <tr>
                  <td class="content text-left">
                    <div class="p">Column two</div>
                  </td>
                </tr>
              </table>
            </div>
            <!--[if (gte mso 9)|(IE)]></td></tr></table><![endif]-->
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>
```

<a name="imgcol"/>

#### Images columns
Images need to be handled slightly differently then text content, as such, there are a few adjustments to accomodate this.

* `.media-fill` (fill container) and `.media-padded` (space around image) classes on wrapping `<td>`
* `<table>` housing the image needs to be set to `align='center'`
* `.text-middle` and  `valign="middle"` replace `top` values (if you want vertically alignmed middle).

```HTML
<table class="module two-col">
  <tr>
    <td class="frame">
      <table class="pane">
        <tr>
          <td class="text-center text-middle">
            <!--[if (gte mso 9)|(IE)]><table align="center" bgcolor="#ffffff" border="0" cellpadding="0" cellspacing="0" width="100%"><tr><td align="center" style="font-size:0" valign="middle" width="50%"><![endif]-->
            <div class="col col-fill text-middle">
              <table align="center">
                <tr>
                  <td class="media-fill text-center">
                  <!--or <td class="media-padded text-center"> if you want some space around your image -->
                    <img src="https://placehold.it/320x400" width="320" height="400" alt>
                  </td>
                </tr>
              </table>
            </div>
            <!--[if (gte mso 9)|(IE)]></td><td align="center" style="font-size:0" valign="middle" width="50%"><![endif]-->
            <div class="col col-fill text-middle">
              <table>
                <tr>
                  <td class="content text-left">
                    <div class="p">Column w/ Image</div>
                  </td>
                </tr>
              </table>
            </div>
            <!--[if (gte mso 9)|(IE)]></td></tr></table><![endif]-->
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>
```

<a name="altcol"/>

#### Alternating columns
To alternate columns, utilize the `dir="rtl"` attribute on the `.pane td`, you will need to reset the direction on the `.content` wrapper so your text displays correctly. All we're doing is inverting the containers. This will be advantageous when you have images to the left or right of text, but want those images to alternate down the page.

```HTML
<table class="pane">
  <tr>
    <td class="text-center text-top" dir="rtl">
... 
      <td class="content text-left" dir="ltr">
...

```

<a name="threecol"/>

#### Three column modules
This is identical to the two column modules, the below snippet would be added directly following the last `.col` closing `</div>` and then updating the widths as you did in the `.two-col` module. 

* adding a `.three-col` in place of the `.two-col` class on the `.module` wrapper will apply a max-width `.col` class allowing space for 3 columns.
* conditional comments `<td>` gets a `width="33.333%"` to accomodate Outlook Express engine clients.

```HTML
<table class="module two-col">
...
<!--[if (gte mso 9)|(IE)]></td><td align="center" style="font-size:0" valign="top" width="33.333%"><![endif]-->
<div class="col col-fill text-top">
  <table>
    <tr>
      <td class="content text-left">
        <div class="p">Column three</div>
      </td>
    </tr>
  </table>
</div>
...
```

**As I'm sure you've noticed, the bulk of the code is reusable as you apply varying columns down the page**

---

#### Support
- Outlook 2002-2016, outlook.com & Windows Mail (Outlook Express & DPI versions **are supported**)
- Yahoo Mail
- Lotus 8.5+ (Lotus 7 **not supported**)
- Gmail, New Gmail, & Inbox
- Android 4.4+
- iOS/Apple Mail (All versions)
- AOL Mail

