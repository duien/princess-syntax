# Princess Syntax Theme

A bright syntax theme, with plenty of pink and purple. It's mostly optimized for Ruby, with occasional JavaScript, CSS, and markup. More improvements will probably be coming, but it's also possible I'll get bored and move on. Use at your own risk.

![Ruby syntax example](https://raw.githubusercontent.com/duien/princess-syntax/master/screenshots/ruby_princess.png)

The font used in the screenshot is [Input from FontBureau](http://input.fontbureau.com/preview/?size=14&language=python&theme=monokai&family=InputMono&width=300&weight=300&line-height=1.2&a=0&g=0&i=serifs_round&l=serifs_round&zero=0&asterisk=height&braces=straight&preset=default&customize=please). It's extremely configurable, so I've linked to my particular settings.

If you'd like your current line to be highlighted, you can add the following snippet to your user stylesheet. It's scoped so that it will affect only this syntax theme, and includes an alternate color suggestion for the highlight line as well.

```less
.theme-princess-syntax {
  @pink-light: #ffb1de;
  @blue: #6be5fd;
  
  @current-line-highlight: fade(@blue, 10);
  
  atom-text-editor.is-focused,
  atom-text-editor.is-focused::shadow,
  :host(.is-focused) {
    .line-number.cursor-line {
      background: @current-line-highlight;
    }
    .line.cursor-line {
      background:@current-line-highlight;
    }
  }
}
```

If you'd like the look of the centered indent guides shown in the screenshot, rather than the left-aligned ones that Atom defaults to, you can add the following snippet to your user stylesheet:

```less
atom-text-editor, atom-text-editor::shadow, :host {
  // Shift indent guides to align vertically with center of column
  .indent-guide {
    @indent-offset: 4px; // This might need tweaking depending on font and size
    @guide-width: 1px;
    box-shadow: none;
    background: linear-gradient(90deg, // replace box-shadow with gradient
      transparent,
      transparent @indent-offset,
      @syntax-indent-guide-color @indent-offset,
      @syntax-indent-guide-color @indent-offset + @guide-width,
      transparent @indent-offset + @guide-width)
  }
}
```
