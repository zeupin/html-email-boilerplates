# HTML 邮件模板编写指南

## DOCTYPE

- 使用 xhtml 的格式，对老版本的邮件客户端（特别是 Outlook）兼容性更好。
  ```html
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
  <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
      <title>邮件标题</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    </head>
    <body>
      邮件正文
    </body>
  </html>
  ```
- 因为是 xhtml，`br`,`hr`, `img` 等单元素要注意闭合。
  ```html
  <br />
  <hr />
  <img ... />
  ```

## 样式

- 只能用行内样式，不能用内联样式或者外联样式。
  > 只能用 `style=""` 的行内样式。  
  > 不能用 head 中的 `<style>...</style>` 的内联样式。  
  > 不能使用 `<link rel="stylesheet" type="text/css" href="***.css"/>` 的外联样式。

## 布局

- 用 table 进行布局。
- 如果是固定宽度，table 的宽度最大不要超过 600px，不然会有兼容性问题。
- border 设为 0，行间距和列间距都设为 0，页面居中对齐。
  ```html
  <table border="0" width="100%" cellpadding="0" cellspacing="0" align="center" ...>
    ...
  </table>
  ```
  或
  ```html
  <table border="0" width="600" cellpadding="0" cellspacing="0" align="center" ...>
    ...
  </table>
  ```
- 开发时，可把 `border` 设置为 1，便于查看边界。发布时，把 `border` 改回为 0。
- 不要用 `float`, `position` 等样式。
  > `float` 在 Outlook 中无法识别。

## 图片

- 尽量设置 `width`, `height`，万一图片显示不了，也可以撑起页面。
- `width` 和 `height` 是标准 html 属性，只要写数字，千万不要画蛇添足加 px 等单位。
  ```html
  <img width="200" height="100" alt="bill" title="" src="***.jpg" />
  ```
- 想设置带有单位的 `width` 和 `height` ，必须写在行内样式里面。
- 重要图片一定要设置 `alt`。因为很多 web 邮件默认是不显示图片，设置 `alt` 可以让用户知道图片大致什么内容。
- Outlook 2007-2013 不支持图片的 `margin` 与 `padding` 样式，必要的时候可以用非标准属性 `hspace` 和 `vspace`。
  ```html
  <img vspace="20" hspace="10" src="***.png" />
  ```
