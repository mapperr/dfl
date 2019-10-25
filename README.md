# The DotFiles Linker

A little, dead simple dotfiles linker,

inspired by [bashdot](https://github.com/bashdot/bashdot).

It, well, links your dotfiles to your HOME directory.


## Dotfiles

Just clone this repo, `cd` in it and put your dotfiles in a `dotfiles/default` directory, without the dot.

Then run:

 `dfl link` or `dfl l`

That's it.


It works with dotdirectories:

`dotfiles/default/.config/rofi/config.rasi` will be linked to `$HOME/.config/rasi/config.rasi`

If the path does not exits it will mkdir it for you.

If something that is not a link exists it will ask nicely what to do.

The `dotfiles` directory is gitignored, so, if you didn't do that already, you can `git init` another repo in it.

Or you can symlink your existing dotfiles folder as `/path/to/dfl/dotfiles`.


### Secrets

You can put your secret dotfiles in the `dotfiles/secrets` directory,
they will be linked after the `default` ones, and, if `dotfiles` is a git repo, you can gitignore it.


### Overrides

If you need some 'overrides', put them in a new directory, e.g. `dotfiles/fluxbox`, and pass it to the script as an argument,
like this:

`dfl l fluxbox`

It will link `default`, then `secrets` and then the `fluxbox` directory, overriding existing links.

This way of handle things is inspired by [bashdot](https://github.com/bashdot/bashdot) profiles.

A use case is when you have another pc/server and you need a slightly different configuration,
that translates in you need some dotfiles to have different content than the usual.


### Tracking

`dfl` tracks the links it creates, so it deletes them if they are not presents in your `dotfiles` directory anymore.

It's clean, does not leave broken symlinks all around.


## Utilities

### Git

If you have your dotfiles on some git repo you can do a `dfl clone <your repo>`.
It will clone you repo in the `dotfiles` dir, backupping the existing one.

If you cloned your repo, moved from another directory or just `git init` it
you can commit and push your dotfiles directly with `dfl`:

`dfl git <whatever git command and arguments>`

it `cd` in your `dotfiles` directory and execute the `git` part.

So you can hack your `~/.vimrc` and do:

`dfl g commit -am 'Add awesomeness' && dfl g push`

from wherever you are. Handy, isn't it? : )

### Jumping and dotfiles path

If you have to hack your `overrides` directories, check something, or just dumb around,
you can jump directly in your `dotfiles` directory with `. dfl cd` or `. dfl j`.

Note the dot. I know, dot-this, dot-that, dot-net (eheheh, I'm too funny :-| ).
That dot is there because I cannot change the directory of a parent shell from its child shell.

Another way of doing this is:

    cd `dfl d`

`dfl d` prints your dotfiles directory absolute path.

Ok, it's not that awesome, but, hey, ¯\_(ツ)_/¯.

