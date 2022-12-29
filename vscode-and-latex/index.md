# A Fast Guide on Writing LaTeX with LaTeX Workshop in VS Code


There are dozens of TeX editors so far, such as Texpad and WinEdt.

<!--more-->

After encountered some wired bugs on Texpad,
I decided to use native [TeX Live][texlive] / [MacTex][mactex].
However, TexShop (on macOS) does not have a pretty highlight system.
It seems that the Visual Studio Code is one of the beast choice.

## Step 1. Download & Install TeX Live

Windows users: download `texlive.iso` [here]().

Mac users: download `MacTeX.pkg` [here][mactex_pkg].

Here are some references for the installation:

- [TeX Live on Windows][texlive_win]
- [Installing MacTeX][mactex_install]

For Windows users, after installation,
you should add TeX Live executables to your system `PATH`.

## Step 2. Download & Install Visual Studio Code

You can download it [here][vscode].
The installation is easy.

## Step 3. Install & Configure LaTeX Workshop

Follows the screenshot below to install the extension `LaTeX Workshop`.

![install-extension](https://mathjiajia.github.io/img/install-extension.jpg "install-extension")

After doing that, you may press `Shift` + `Ctrl` + `P` (Windows)
or `Shift` + `Cmd` + `P` (macOS) to show all commands.
Then type `Open User Settings JSON` and open the first item (as shown below).
![open-json](https://mathjiajia.github.io/img/open-json.png "open-json")

Now copy and paste the following two snippets into your `json` file (inside the brackets `{}` of your file).

```json
"latex-workshop.latex.tools": [
 {
  "name": "latexmk",
  "command": "latexmk",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "-pdf",
   "-outdir=%OUTDIR%",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "xelatex",
  "command": "xelatex",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "pdflatex",
  "command": "pdflatex",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "bibtex",
  "command": "bibtex",
  "args": [
   "%DOCFILE%"
  ],
  "env": {}
 }
],
```

```json
"latex-workshop.latex.recipes": [
 {
  "name": "pdfLaTeX",
  "tools": [
   "pdflatex"
  ]
 },
 {
  "name": "latexmk 🔃",
  "tools": [
   "latexmk"
  ]
 },
 {
  "name": "xelatex",
  "tools": [
   "xelatex"
  ]
 },
 {
  "name": "pdflatex ➞ bibtex ➞ pdflatex`×2",
  "tools": [
   "pdflatex",
   "bibtex",
   "pdflatex",
   "pdflatex"
  ]
 },
 {
 "name": "xelatex ➞ bibtex ➞ xelatex`×2",
 "tools": [
   "xelatex",
   "bibtex",
   "xelatex",
   "xelatex"
  ]
 }
]
```

## Step 4. Write & Compile

Now you may open a `tex` file or create a new one.
If you want to compile the file,
press `Ctrl` + `Alt` + `B` (Windows) or `option` + `Cmd` + `B` (macOS).
Moreover, you may choose another recipes from the sidebar.
There is a button in the right top corner to preview `PDF` file.
![tex-recipes](https://mathjiajia.github.io/img/tex-recipes.jpg "tex-recipes")

### Reference: [LaTeX-Workshop Wiki][latex_workshop]

[latex_workshop]: https://github.com/James-Yu/LaTeX-Workshop/wiki
[mactex]: https://www.tug.org/mactex/
[mactex_pkg]: https://mirror.ctan.org/systems/mac/mactex/MacTeX.pkg
[mactex_install]: https://www.tug.org/mactex/mactex-download.html
[texlive]: https://www.tug.org/texlive/
[texlive_iso]: https://mirror.ctan.org/systems/texlive/Images/texlive.iso
[texlive_win]: https://www.tug.org/texlive/windows.html
[vscode]: https://code.visualstudio.com/

