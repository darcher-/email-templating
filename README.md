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

---

### Modules
Majority of your code will be repetative with slight variations, primarily in width's.

#### Single column Module

`.col` doesn't automatically fill empty space, use `.col-fill` to force `100%` width.

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

#### Three column modules
This is identical to the two column modules, the below snippet would be added directly following the last `.col` closing `</div>` and then updating the widths as you did in the `.two-col` module. 

* adding a `.three-col` in place of the `.two-col` class on the `.module` wrapper will apply a max-width `.col` class allowing space for 3 columns.
* conditional comments `<td>` gets a `width="33.333%"` to accomodate Outlook Express engine clients.

```HTML
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

---

#### Support
- Outlook 2002-2016, outlook.com & Windows Mail (Outlook Express & DPI versions **are supported**)
- Yahoo Mail
- Lotus 8.5+ (Lotus 7 **not supported**)
- Gmail, New Gmail, & Inbox
- Android 4.4+
- iOS/Apple Mail (All versions)
- AOL Mail

