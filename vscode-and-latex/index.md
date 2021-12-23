# A Fast Guide on Writing LaTeX with LaTeX Workshop in VS Code


There are dozens of TeX editors so far, such as Texpad and WinEdt.

<!--more-->

After encountered some wired bugs on Texpad, I decided to use native [TeX Live](https://www.tug.org/texlive/) / [MacTex](https://www.tug.org/mactex/).
However, TexShop (on macOS) does not have a pretty highlight system.
It seems that the Visual Studio Code is one of the beast choice.

## Step 1. Download & Install TeX Live

Windows users: download `texlive.iso` [here](https://download.nus.edu.sg/mirror/ctan/systems/texlive/Images/).

Mac users: download `MacTeX.pkg` [here](https://mirror.ctan.org/systems/mac/mactex/MacTeX.pkg).

Here are some references for the installation:

- [TeX Live on Windows](https://www.tug.org/texlive/windows.html)
- [Installing MacTeX](https://www.tug.org/mactex/mactex-download.html)

For Windows users, after installation, you should add TeX Live executables to your system `PATH`.

## Step 2. Download & Install Visual Studio Code

You can download it [here](https://code.visualstudio.com/).
The installation is easy.

## Step 3. Install & Config LaTeX Workshop

Follows the screenshot below to install the extension `LaTeX Workshop`.

![install-extension](https://mathjiajia.github.io/img/install-extension.jpg "install-extension")

After doing that, you may press `Shift` + `Ctrl` + `P` (Windows) or `Shift` + `cmd` + `P` (macOS) to show all commands.
Then type `Open Settings JSON` and open the first item (as shown below).
![open-json](https://mathjiajia.github.io/img/open-json.jpg "open-json")

Now copy and paste the following to your `json` file (inside the brackets `{}`).

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
If you want to compile the file, press `Ctrl` + `Alt` + `B` (Windows) or `option` + `cmd` + `B` (macOS).
Moreover, you may choose another recipes from the sidebar.
There is button in the right top corner to preview `PDF` file.
![tex-recipes](https://mathjiajia.github.io/img/tex-recipes.jpg "tex-recipes")

### Reference: [LaTeX-Workshop Wiki](https://github.com/James-Yu/LaTeX-Workshop/wiki)

