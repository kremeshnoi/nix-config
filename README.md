# Nix Config

NixOS under WSL and a Mac with nix-darwin, built from one flake with one home-manager setup. It lives as the `nix/` submodule of [dotfiles](https://github.com/kremeshnoi/dotfiles) and takes the OS-independent configs from that repo's `shared/` through the `dotfiles` flake input.

```
flake.nix   nixosConfigurations.nixos, darwinConfigurations.mac
home/       shared home-manager modules and the shared package list
  nixos/    NixOS only
  darwin/   Mac with Nix only
nixos/      the NixOS-WSL system
darwin/     the nix-darwin system
pkgs/       release binaries: herdr, lazygit, delta, phpantom
```

## Use

```bash
git clone --recurse-submodules git@github.com:kremeshnoi/dotfiles.git ~/dev/dotfiles
nh os switch
nh darwin switch
```

A change to `shared/` in dotfiles reaches a machine after `nix flake update dotfiles` here. To try it from the local checkout first:

```bash
nh os switch -- --override-input dotfiles git+file:$HOME/dev/dotfiles
```

The docs live in [dotfiles/docs](https://github.com/kremeshnoi/dotfiles/tree/main/docs).
