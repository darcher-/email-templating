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

**Layout code block description:**
Majority of your code will be repetative with slight variations, primarily in width's.

```HTML

<table>
  <tr>
    <td>
      <!--[if (gte mso 9)|(IE)]>
      <table align="center" bgcolor="{{six digit hex color e.g. #ffffff}}" border="0" cellpadding="0" cellspacing="0" width="{{pixel value width e.g. 640}}">
        <tr>
          <td align="center" style="font-size:0;" valign="top" width="{{percent value width e.g. 100%}}">
      <![endif]-->

      <div>
        <table>
          <tr>
            <td>
              <div>...</div>
            </td>
          </tr>
        </table>
      </div>
  
      <!--[if (gte mso 9)|(IE)]>
          </td>
        </tr>
      </table>
      <![endif]-->
    </td>
  </tr>
</table>

```
