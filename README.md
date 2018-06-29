# modern-email
A modern approach to email templating

**requires use of inliner (e.g. https://putsmail.com/inliner or Litmus inlining tool)**

##### Support
- Outlook 2002-2016, outlook.com & Windows Mail (Outlook Express & DPI versions **are supported**)
- Yahoo Mail
- Lotus 8.5+ (Lotus 7 **not supported**)
- Gmail, New Gmail, & Inbox
- Android 4.4+
- iOS/Apple Mail (All versions)
- AOL Mail

###### To Do
- [x] initial upload of base layout and elements
- [ ] inlined versions
- [ ] create various themes for template
- [ ] additional element styling
- [ ] additional modules

######Modules
Majority of your code will be repetative with slight variations, primarily in width's.

+ `.col` container will only need an additional class if it's a sidebar or uneven width.
+ conditional comment `<td>` will require a `width` attribute with a `%` value if more than one column is present.
+ `.two-col` and `.three-col` adjusts `max-width` values, but conditional comment `<td>`'s values will need to update to `50%` or `33.333%` respectively (if offset, e.g. sidebars, the larger column's `<td>` will need a width of `66.666%`).

```HTML
<table class="module sidebar-left bordered">
  <tr>
    <td>
      <table class="inner">
        <!--[if (gte mso 9)|(IE)]><table align="center" bgcolor="#ffffff" border="0" cellpadding="0" cellspacing="0" width="638"><tr><td align="center" style="font-size:0" valign="top""><![endif]-->
        <div class="col col-fill text-top">
          <table>
            <tr>
              <td class="content text-left">
                <div class="p">
...
```

---

######Alternating columns
To alternate columns, utilize the `dir="rtl"` attribute, you will need to reset the direction on the `.content` wrapper, you just want to invert the containers.

```HTML
<table class="inner">
  <tr>
    <td class="text-center text-top" dir="rtl">
... 
      <td class="content text-left" dir="ltr">
...

```
