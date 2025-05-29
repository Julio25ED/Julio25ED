<span style="color: green; font-size: 20px;">Hello World, I'm Julio, be very welcome</span>

<table>
   <a href="https://github.com/Julio25ED">

 <img src="https://img.icons8.com/color/2x/html-5.png" width="120" alt="HTML5">
  
  <img src="https://img.icons8.com/color/2x/css3.png" width="120" alt="CSS3">
  
   <img src="https://img.icons8.com/nolan/2x/javascript.png" width="120" alt="JavaScript">

   <img src = "https://img.icons8.com/?size=100&id=Pd2x9GWu9ovX&format=png&color=000000" width="120" alt="JAVA">
   
</table>
<div>
 <a href="https://github.com/"julio25ed>
 <img height="180em" src="https://github-readme-stats.vercel.app/api?username=julio25ed&show_icons=true&theme=dark&include_all_commits=true&count_private=true"/>
 <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=julio25ed&layout=compact&langs_count=7&theme=dark"/>
</div>

## 🌐 Socials:
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/Jdesz_) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/juliodev25) 

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}




