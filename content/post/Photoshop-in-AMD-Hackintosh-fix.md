---
title: "Photoshop in AMD Hackintosh Fix" # Title of the blog post.
date: 2020-08-09T13:12:29+03:00 # Date of post creation.
description: "Article description." # Description used for search engine.
featured: true # Sets if post is a featured post, making appear on the home page side bar.
draft: false # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
# menu: main
featureImage: "/images/amd-osx.jpeg" # Sets featured image on blog post.
thumbnail: "/images/amd-osx.jpeg" # Sets thumbnail image appearing inside card on homepage.
shareImage: "/images/path/share.png" # Designate a separate image for social media sharing.
codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
categories:
  - Hackintosh
tags:
  - Photoshop
  - Turorial
  - AMD
---

De ceva timp (mai exact din 12 Iulie 2020) folosesc sistemul de operare de la Apple, Mac OS Catalina pe un PC cu un procesor AMD Ryzen 3 3700X @4.2Ghz, 16GB RAM, Radeon RX590 Nitro de la Sapphire pe un SSD Samsung NVME de 512GB totul bagat intr-o carcasa Thermaltake Core V1. Per total e un sistem de care sunt tare mandru si care ruleaza de vis pe un monitor Samsung 4K rezolutie.

Problema este ca avand un [Hackintosh](https://en.wikipedia.org/wiki/Hackintosh), nu vine fara probleme si probleme sunt destule dar asta e partea faina la un Hackintosh. Daca esti o persoana ca mine, cum zic americanii "_tinkerer_" adica unul caruia ii place sa bibileasca pana cand reuseste, atunci Hackintosh este penru tine la fel ca si Linuxul. Dar sa revenim la problema noastra.

Desi platesc o subscriptie lunara la Adobe pentru Lightroom si Photoshop, Photoshop refuza sa mearga din prima pe un AMD Hackintosh, stiu ca pe Intel merge din prima fara probleme. Asa ca am sapat pe net si am gasit solutia.

Depinde de versiunea pe care o rulati am sotutia pentru toate. Deschideti terminalul si copiati urmatoarele:

### PS 2018 :  
`sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x5A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' /Applications/Adobe\ Photoshop\ CC\ 2018/Adobe\ Photoshop\ CC\ 2018.app/Contents/Required/Plug-ins/Extensions/MMXCore.plugin/Contents/MacOS/MMXCore`
`sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x5A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' /Applications/Adobe\ Photoshop\ CC\ 2018/Adobe\ Photoshop\ CC\ 2018.app/Contents/Required/Plug-ins/Extensions/FastCore.plugin/Contents/MacOS/FastCore`
### PS 2019 :
`sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x6A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' /Applications/Adobe\ Photoshop\ CC\ 2019/Adobe\ Photoshop\ CC\ 2019.app/Contents/Required/Plug-ins/Extensions/MMXCore.plugin/Contents/MacOS/MMXCore`
`sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x6A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' /Applications/Adobe\ Photoshop\ CC\ 2019/Adobe\ Photoshop\ CC\ 2019.app/Contents/Required/Plug-ins/Extensions/FastCore.plugin/Contents/MacOS/FastCore`
### PS 2020 :
`sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x6A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' /Applications/Adobe\ Photoshop\ 2020/Adobe\ Photoshop\ 2020.app/Contents/PlugIns/Required/Extensions/MMXCore.plugin/Contents/MacOS/MMXCore`
`sudo perl -i -pe 's|\x90\x90\x90\x90\x56\xE8\x6A\x00|\x90\x90\x90\x90\x56\xE8\x3A\x00|sg' /Applications/Adobe\ Photoshop\ 2020/Adobe\ Photoshop\ 2020.app/Contents/PlugIns/Required/Extensions/FastCore.plugin/Contents/MacOS/FastCore`
## Photoshop Font Crash :
### PS 2018 :
`sudo rm -rf /Applications/Adobe\ Photoshop\ CC\ 2018/Adobe\ Photoshop\ CC\ 2018.app/Contents/Required/Deep_Font`
### PS 2019 :
`sudo rm -rf /Applications/Adobe\ Photoshop\ CC\ 2019/Adobe\ Photoshop\ CC\ 2019.app/Contents/Required/Deep_Font`
### PS 2020 :
`sudo rm -rf /Applications/Adobe\ Photoshop\ 2020/Adobe\ Photoshop\ 2020.app/Contents/Required/Deep_Font`

Succes.
