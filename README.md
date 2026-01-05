# rich-preview.yazi

Preview file types using `rich` command in Yazi. This plugin allows preview for various filetypes including -

- Markdown
- Jupyter notebook
- JSON
- CSV
- RestructuredText

## Previews/Screenshots

[rich-preview1.webm](https://github.com/user-attachments/assets/580e36a8-249f-48a8-95fc-8c3d60e6a7d7)

## Requirements

- [Yazi](https://github.com/sxyazi/yazi) v25.4.8 or higher.
- [rich-cli](https://github.com/Textualize/rich-cli) v13.7.1 or higher.

## Installation

To install this plugin, simply run-

```bash
ya pkg add AnirudhG07/rich-preview
## For linux and MacOS
git clone https://github.com/AnirudhG07/rich-preview.yazi.git ~/.config/yazi/plugins/rich-preview.yazi

## For Windows
git clone https://github.com/AnirudhG07/rich-preview.yazi.git %AppData%\yazi\config\plugins\rich-preview.yazi
```

## Usages

The `rich` commands automatically detects if the file is markdown, csv, json, etc. files and accordingly the preview is viewed.

Add the below to your `yazi.toml` file to allow the respective file to previewed using `rich`.

```toml
[plugin]

prepend_previewers = [
    { url = "*.csv", run = "rich-preview"}, # for csv files
    { url = "*.md", run = "rich-preview" }, # for markdown (.md) files
    { url = "*.rst", run = "rich-preview"}, # for restructured text (.rst) files
    { url = "*.ipynb", run = "rich-preview"}, # for jupyter notebooks (.ipynb)
    { url = "*.json", run = "rich-preview"}, # for json (.json) files
#    { url = "*.lang_type", run = "rich-preview"} # for particular language files eg. .py, .go., .lua, etc.
]
```

## Configurations

If you would like to use `rich` with more configurations, you can go to `init.lua` and edit the arguments in the code with your preferences. You can view the options using `rich --help`.

```lua
-- init.lua
"-j",
"--left",
"--line-numbers",
"--force-terminal",
"--panel=rounded",
"--guides",
"--max-width" -- to area of preview
```

You can add more, remove and choose themes as you wish. You can set styles or Themes(as mentioned in `rich --help`) by `--theme=your_theme` and similarly for style.

## Notes

Currently the colors maynot be uniformly present, along with weird lines here and there. This is due to `"--force-terminal"` option. You can disable it if you find it annoying. Work is in progress to possibly fix the issue.

## Using piper.yazi

[piper.yazi](https://github.com/yazi-rs/plugins/tree/main/piper.yazi) is a general-purpose previewer - you can pass any shell command to piper and it will use the command's output as the preview content.

To use `rich` with piper, you can add this in your `yazi.toml` file:

```toml
[[plugin.prepend_previewers]]
url = "*.md"
run  = 'piper -- rich -j --left --panel=rounded --guides --line-numbers --force-terminal "$1"'
```

Note you can also add other filetypes as mentioned above in the same format.

# Explore Yazi

Yazi is an amazing, blazing fast terminal file manager, with a variety of plugins, flavors and themes. Check them out at [awesome-yazi](https://github.com/AnirudhG07/awesome-yazi) and the official [yazi webpage](https://yazi-rs.github.io/).
