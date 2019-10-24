A little dotfiles linker.

It links your dotfiles to your HOME directory.

### Dotfiles

Just put your dotfiles in a `dotfiles/default` directory, without the dot.

The `dotfiles` directory is gitignored, so you can `init` another git repo in it.

You can put your secret dotfiles in the `dotfiles/secrets` directory, they will be linked after the `default` ones,
and, if `dotfiles` is a git repo, you can gitignore it.

If you need some 'overrides', put them in a new directory and pass it to the script as an argument,
like this:

`./dfl fluxbox`

It will link `default`, then `secrets` and then the `fluxbox` directory, overriding existing links.

It works with directories too:

`dotfiles/default/.config/rofi/config.rasi` will be linked to `$HOME/.config/rasi/config.rasi`

If the path does not exits it will mkdir it for you.

If something that is not a link exists it will ask nicely what to do.


As for now, there no merging of default and overrides files:
it seems a pain in the ass to me, with only a little gain.

### Git

You can commit and push your dotfiles directly with `dfl`!

Just:

`dfl git <whatever git command and arguments>`

it `cd` in your `dotfiles` directory and execute the `git` part.

Handy, isn't it? : )

