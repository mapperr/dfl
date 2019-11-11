# The DotFiles Linker

A little, dead simple dotfiles linker,

inspired by [bashdot](https://github.com/bashdot/bashdot).

It, well, links your dotfiles to your HOME directory.


## Dotfiles

Just put the `dfl` scrpt in your `PATH`, and put your dotfiles in a `~/.dfl/dotfiles/default` directory, without the dot.

Then run:

 `dfl link` or `dfl l`

That's it.


It also works with files in dotdirectories:

`dotfiles/default/.config/rofi/config.rasi` will be linked to `$HOME/.config/rasi/config.rasi`

If the path does not exits it will mkdir it for you.

If something that is not a link exists it will ask nicely what to do.


### Secrets

You can put your secret dotfiles in the `dotfiles/secrets` directory,
they will be linked after the `default` ones and the eventual override.

It's a handy directory to gitignore, if your `dotfiles` is a git repo.


### Overrides

Or 'profiles' if it suits you better.

If you need some 'overrides', put them in a new directory,
e.g. `dotfiles/fluxbox`, and pass it to the script as an argument,
like this:

`dfl l fluxbox`

It will link `default`, then the `fluxbox` and then `secrets`, overriding existing links.

This way of handle things is inspired by [bashdot](https://github.com/bashdot/bashdot) profiles.

A use case is when you have another pc/server and you need a slightly different configuration,
that translates in you need some dotfiles to have different content than the usual.


### Auto override

You can make dfl choose a profile automatically so that you don't have
to remember to type it if you set the env var `DFL_OVERRIDE`.
If `dfl` does not find that var, it checks if there is a profile dir named
as the output of the hostname command and take that as the profile.


### Tracking

`dfl` tracks the links it creates,
so it deletes them if they are not presents in your `dotfiles` directory anymore.

It's clean, does not leave broken symlinks all around.


## Utilities


### Take

Spotted a file that you shold move to your dotfiles?

`dfl take .config/gopass/config.yml`

it moves that file into your `default` profile, recreating the relative directory structure.

It works with dotdirectories and you can specify an `override`, like:

`dfl t .fluxbox fluxbox`

It moves the `.fluxbox` directory into `<dotfiles_dir>/fluxbox/fluxbox`

After that you only need to link them up with `dfl l`.


### Git

If you have your dotfiles on some git repo you can do a `dfl clone <your repo>`.
It will clone you repo in the `dotfiles` dir, backupping the existing one.

So, if your dotfiles dir is a git repo you can commit and push your dotfiles
directly with `dfl`:

`dfl git <whatever git command and arguments>`

it `cd`s in your `dotfiles` directory and executes the `git` part.

For example, you can hack your `~/.vimrc` and do:

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

Ok, it's not that awesome, but, hey, ¯\\_(ツ)_/¯.

