# Extended Void Packages Collection

This is an unofficial repository, that contains xbps-src templates (as in void-linux/void-packages) of applications either not being accepted in the official repository due to various reasons (including quality standards which require packages to be tagged/released as versions) or needs more work done to be in the official repository.

It is primarily intended for my private use.


## Usage (binary packages / repository)

Add the following mirror:
```bash
echo 'repository=https://animeshz-void-xpackages.netlify.app' | sudo tee /etc/xbps.d/11-repository-xpack.conf
sudo xbps-install -S
```

Package should now be indexed and be available from any `xbps` command.


## Usage (build locally / xbps-src)

Just add upstream and merge this into your void-packages clone, and [build as usual](https://github.com/void-linux/void-packages#quick-start).

```bash
git remote add --fetch xpackages https://github.com/Animeshz/void-xpackages
git merge -s subtree -Xsubtree=srcpkgs xpackages/main --allow-unrelated-histories --no-edit

# To see a list of packages coming from this repository
git ls-tree -d --name-only xpackages/main

# Build & Install (xbps-src) see link above for more information
./xbps-src pkg <pkgname>
sudo xbps-install -R hostdir/binpkgs <pkgname>

# (Optional) Add that repository as a mirror, so for not passing '-R' everytime for every xbps command
echo "repository=$PWD/hostdir/binpkgs" | sudo tee /etc/xbps.d/11-repository-xpack.conf
```


## Work on / Add stuffs

Work primarily on your void-packages clone to keep testing, and then move the final changes to this repository:

```bash
mv /path/to/void-packages/srcpkgs/<pkg> /path/to/xpackages-clone
```
