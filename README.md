# emuflight.github.io

Website made using Github pages with Jekyll. 

Theme used: [Just-The-Docs](https://github.com/pmarsceill/just-the-docs)

## Jekyll setup for Windows WSL or Linux: 


### Install Ruby and other [prerequisites](https://jekyllrb.com/docs/installation/#requirements):

```shell
sudo apt-get install ruby-full build-essential zlib1g-dev
```
Avoid installing RubyGems packages (called gems) as the root user. Instead, set up a gem installation directory for your user account. The following commands will add environment variables to your ```~/.bashrc``` file to configure the gem installation path:
```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
```
```
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
```
```
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
```
Default Terminal:
```
source ~/.bashrc
```
Or ZSH terminal:
```
source ~/.zshrc
```

Finally, install Jekyll and Bundler:
```
gem install jekyll bundler
```

Clone Repository
```
git clone git@github.com:emuflight/emuflight.github.io.git
```
```
cd emuflight.github.io
```
To set up your environment to develop
```
bundle install
```
To test your theme, run
```
bundle exec jekyll serve
```
Open your browser to: http://localhost:4000 , As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

Developers with write-access to the repo, should perferrm the following for live updates:
```
bundle update github-pages
git add -u ; git commit ; git push
```
---
Official Jekyll setup page for: [Windows/MacOS/Ubuntu/Other Linux](https://jekyllrb.com/docs/installation/#requirements)
