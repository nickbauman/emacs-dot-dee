# Nick Bauman's Personal Emacs Config

I added neo-tree to the brave clojure setup. I've also upgraded many of the packages used in the brave clojure setup.

## This is a Clojure-friendly emacs config, with some golang support, such as it is.

If you're new to emacs, check out
[this introductory tutorial](http://www.braveclojure.com/basic-emacs/)!

The TL;DR here is install emacs (NOT AquaMacs) and copy this repo to `~/.emacs.d` replacing the existing one if it exists, then launch emacs. `F8` will launch a file browser in its own pane.

## Organization

I've tried to separate everything logically and document the purpose
of every line. [`init.el`](./init.el) acts as a kind of table of
contents.  It's a good idea to eventually go through `init.el` and the
files under the `customizations` directory so that you know exactly
what's going on.

## Supporting CSS, HTML, JS, etc.

Emacs has decent support for CSS, HTML, JS, and many other file types out of the box, but if you want better support, then have a look at [my personal emacs config's init.el](https://github.com/flyingmachine/emacs.d/blob/master/init.el). It's meant to read as a table of contents. The emacs.d as a whole adds the following:

* [Customizes js-mode and html editing](https://github.com/flyingmachine/emacs.d/blob/master/customizations/setup-js.el)
    * Sets indentation level to 2 spaces for JS
    * enables subword-mode so that M-f and M-b break on capitalization changes
    * Uses `tagedit` to give you paredit-like functionality when editing html
    * adds support for coffee mode
* [Uses enh-ruby-mode for ruby editing](https://github.com/flyingmachine/emacs.d/blob/master/customizations/setup-ruby.el). enh-ruby-mode is a little nicer than the built-in ruby-mode, in my opinion.
    * Associates many filenames and extensions with enh-ruby-mode (.rb, .rake, Rakefile, etc)
    * Adds keybindings for running specs
* Adds support for YAML and SCSS using the yaml-mode and scss-mode packages

In general, if you want to add support for a language then you should be able to find good instructions for it through Google. Most of the time, you'll just need to install the "x-lang-mode" package for it.

## Supporting GO somewhat

The golang support was derived from the following blog post:
http://tleyden.github.io/blog/2014/05/22/configure-emacs-as-a-go-editor-from-scratch/

Needless to say, far from all of that is used here. You will need to follow these steps at least for installing `go-mode:`

* Start with `mkdir -p ~/misc/emacs && cd ~/misc/emacs`
* Then `git clone git@github.com:dominikh/go-mode.el.git` or if you prefer `https://github.com/dominikh/go-mode.el.git`
* From within Emacs, run `M-x update-file-autoloads`, point it at the `go-mode.el` file in the cloned directory. Emacs will prompt you for a result path, and you should enter `~/misc/emacs/go-mode.el/go-mode-load.el`
* Add these two lines to your `~/.emacs.d/init.d`
    (add-to-list 'load-path "~/Misc/emacs/go-mode.el/")
    (require 'go-mode-load)

