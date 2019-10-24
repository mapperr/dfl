A little, dead simple dotfiles linker,

inspired by [bashdot](https://github.com/bashdot/bashdot).

It, well, links your dotfiles to your HOME directory.


## Dotfiles

Just clone this repo, `cd` in it and put your dotfiles in a `dfl/dotfiles/default` directory, without the dot.

The `dotfiles` directory is gitignored, so you can even `git init` another repo in it.

Or you can symlink your existing dotfiles folder as `/path/to/dfl/dotfiles`.

So, to create links run:

`dfl link`

It works with directories too:

`dotfiles/default/.config/rofi/config.rasi` will be linked to `$HOME/.config/rasi/config.rasi`

If the path does not exits it will mkdir it for you.

If something that is not a link exists it will ask nicely what to do.


### Secrets

You can put your secret dotfiles in the `dotfiles/secrets` directory,
they will be linked after the `default` ones, and, if `dotfiles` is a git repo, you can gitignore it.


### Overrides

If you need some 'overrides', put them in a new directory, e.g. `dotfiles/fluxbox`, and pass it to the script as an argument,
like this:

`dfl link fluxbox`

It will link `default`, then `secrets` and then the `fluxbox` directory, overriding existing links.

This way of handle things is inspired by [bashdot](https://github.com/bashdot/bashdot) profiles.

A use case is when you have another pc/server and you need a slightly different configuration,
that translates in you need some dotfiles to have different content than the usual.


## Git

You can commit and push your dotfiles directly with `dfl`!

Just:

`dfl git <whatever git command and arguments>`

it `cd` in your `dotfiles` directory and execute the `git` part.

Handy, isn't it? : )

