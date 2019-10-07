# Eisvogel-pdf
## Setup
### *Docker environment*

I used the docker image from [@cagix/pandoc-thesis](https://github.com/cagix/pandoc-thesis)


- Install Docker on Windows
- Install WSL (Windows System for Linux)
   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
   ```
- Search `Microsoft Store` for Ubuntu
- Follow [this](https://nickjanetakis.com/blog/setting-up-docker-for-windows-and-wsl-to-work-flawlessly) guide for access `Docker daemon` on Windows
- Finally run `make docker`

After this steps you should have a pandoc-thesis docker image.
Check with `docker images`

### *Download Eisvogel*
Download Eisvogel from [@Wandmalfarbe/pandoc-latex-template](https://github.com/Wandmalfarbe/pandoc-latex-template/releases)

### *Build a PDF*
```
docker run --rm -v /c/your/path:/pandoc pandoc-thesis pandoc
           -f markdown
           --pdf-engine=pdflatex
           --filter=pandoc-citeproc
           --resource-path "./images/"
           --listings
           --template=eisvogel.tex
           -M eisvogel=true
           -o test.pdf
           basic-example.md
```