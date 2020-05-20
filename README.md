# rusty-tools

## Organizations utilizing rust tools

<https://discussion.fedoraproject.org/t/tools-applications-written-in-rust/1040>

<https://fedoramagazine.org/oxidizing-fedora-try-rust-applications-today/>

<https://www.reddit.com/r/rust/comments/cap9ul/debian_10_released_contains_ripgrep_fdfind_exa/>

<https://www.debian.org/releases/stable/amd64/release-notes/ch-whats-new.en.html#newdistro>

<https://msrc-blog.microsoft.com/2019/11/07/using-rust-in-windows/>

<https://barcelona.rustfest.eu/sessions/r-evolution>

<https://www.zdnet.com/article/microsoft-opens-up-rust-inspired-project-verona-programming-language-on-github/>

## Sample tools

Many of these tools have similar, attractive themes:

1. Speed

2. Reasonable defaults

3. Active development

<https://github.com/imsnif/bandwhich>

<https://github.com/sharkdp/bat>

<https://github.com/Canop/broot>

<https://github.com/ogham/exa>

<https://github.com/sharkdp/fd>

<https://github.com/timvisee/ffsend>

<https://github.com/sharkdp/hexyl>

<https://github.com/Peltoche/lsd>

<https://github.com/str4d/rage>

<https://github.com/BurntSushi/ripgrep>

<https://github.com/chmln/sd>

<https://github.com/XAMPPRocky/tokei>

## bandwhich

```bash
bandwhich -h

sudo bandwhich
```

## bat

```bash
bat -h

bat ~/.zshrc

# Show non-printable characters.
bat -A /etc/hosts

# Show content of an online script.
curl -s https://sh.rustup.rs | bat
curl -s https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh | bat
```

## broot

```bash
broot

Broot should be launched using a shell function (see https://github.com/Canop/broot for explanations).
The function is either missing, old or badly installed.
Can I install it now? [Y n]
y
Writing br shell function in /Users/madden/Library/Application Support/org.dystroy.broot/launcher/bash/1.
Creating link from /Users/madden/Library/Preferences/org.dystroy.broot/launcher/bash/br to /Users/madden/Library/Application Support/org.dystroy.broot/launcher/bash/1.
/Users/madden/.bash_profile already patched, no change made.
/Users/madden/.zshrc already patched, no change made.

The br function has been installed.
You may have to restart your shell or source your shell init files.
Afterwards, you should start broot with br in order to use its full power.
```

```bash
br
```

## exa

```bash
exa --help

# Display one entry per line.
exa -1

# Show hidden and 'dot' files.
exa -a

# Display extended file metadata as a table.
# Sort newest files.
exa -l -snew
```

## fd

```bash
fd -h

# Find files in a project.
cd ~/src/mikemadden42
fd linpack

# Find all files with a certain name.
fd passwd /etc

# Find files with a certain extension.
cd ~/src/mikemadden42/beats-tester
fd -e yml

# Find & remove certain files.
# https://en.wikipedia.org/wiki/.DS_Store
fd -H '^\.DS_Store$' -tf
fd -H '^\.DS_Store$' -tf -X rm
```

## ffsend

```bash
ffsend -h

# Upload a file.
ffsend upload cat.jpg

# Check if a resource exists.
ffsend exists URL

# Get info on a resource.
ffsend info URL

# Delete a resource.
ffsend delete URL

# Set the password on a resource.
ffsend password URL

# Download a resource.
ffsend download URL
```

## hexyl

```bash
hexyl -h

# Show first 256 bytes of a file.
hexyl -n 256 cat.jpg
```

## lsd

<https://github.com/Peltoche/lsd/issues/199#issuecomment-494218334>

```bash
lsd --help

# Display one entry per line.
lsd -1

# Do not ignore entries starting with a dot.
lsd -a

# Display extended file metadata as a table.
lsd -l

# For ls compatibility purposes ONLY, currently set by default.
lsd -lh

# Sort by time modified.
lsd -lht

# Reverse the order of the sort.
lsd -lhrt
```

## rage

```bash
rage -h

# Encrypt with a passphrase instead of recipients.
rage -p -o cat.jpg.age cat.jpg

# Decrypt the input.
rage -d cat.jpg.age > cat2.jpg

# Calculate hash for cat images.
gsha1sum cat*.jpg

# Encrypt to a PEM encoded format.
rage -p -a -o cat2.jpg.age cat.jpg

# Display a PEM encoded file.
bat cat2.jpg.age
```

## rg

```bash
rg -h
```

Recursively searching your current working directory is the default mode of operation for ripgrep.
This repo has over 21 million lines of code and comments.  rg finds results in under a couple seconds.

```bash
cd ~/src/elastic/endpoint-dev
rg GetComputerName
```

By default, when you search a directory, ripgrep will ignore all of the following:

- Files and directories that match the rules in your .gitignore glob pattern.
- Hidden files and directories.
- Binary files. (ripgrep considers any file with a NUL byte to be binary.)
- Symbolic links aren't followed.

All of these things can be toggled using various flags provided by ripgrep:

- You can disable .gitignore handling with the `--no-ignore` flag.
- Hidden files and directories can be searched with the `--hidden` flag.
- Binary files can be searched via the `--text` (`-a` for short) flag. Be careful with this flag! Binary files may emit control characters to your terminal, which might cause strange behavior.
- ripgrep can follow symlinks with the `--follow` (`-L` for short) flag.

```bash
-i/--ignore-case: When searching for a pattern, ignore case differences. That is rg -i fast matches fast, fASt, FAST, etc.
-C/--context: Show the lines surrounding a match.
```

<https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md>

## sd

```bash
sd -h

# Search and replace all occurances of 1.13.10 with 1.13.11.
sd 1.13.10 1.13.11 README.md
sd 1.13.10 1.13.11 go1.13/Makefile.common
sd 1.13.10 1.13.11 go1.13/base/Dockerfile.tmpl
sd 8a4cbc9f2b95d114c38f6cbe94a45372d48c604b707db2057c787398dfbf8e7f a4d71ca9e02923fa96669a4b5faf78ee8331b18e7209b09dd87fe763b4838ada go1.13/base/Dockerfile.tmpl

# Search and replace all occurances of 1.14.2 with 1.14.2.
sd 1.14.2 1.14.3 README.md
sd 1.14.2 1.14.3 go1.14/Makefile.common
sd 1.14.2 1.14.3 go1.14/base/Dockerfile.tmpl
sd 6272d6e940ecb71ea5636ddb5fab3933e087c1356173c61f4a803895e947ebb3 1c39eac4ae95781b066c144c58e45d6859652247f7515f0d2cba7be7d57d2226 go1.14/base/Dockerfile.tmpl
```

## tokei

<https://github.com/AlDanial/cloc>

<https://dwheeler.com/sloccount/>

<https://github.com/hhatto/gocloc>

<https://github.com/boyter/scc>

```bash
tokei -h

# Prints out supported languages and their extensions.
tokei -l

cd ~/src/elastic/endpoint-dev

# Show lines of code.
tokei

# Sort by lines of code.
tokei -slines .

# Only count common markup languages.
tokei -t JSON,TOML,YAML,XML .
```

## Other projects

<https://github.com/trending/rust?since=daily>

<https://github.com/alacritty/alacritty>

<https://github.com/m4b/bingrep>

<https://github.com/RustSec/cargo-audit>

<https://github.com/matthiaskrgr/cargo-cache>

<https://github.com/kbknapp/cargo-outdated>

<https://github.com/DevinR528/cargo-sort-ck>

<https://github.com/tbrand/cargo-tomlfmt>

<https://github.com/sfackler/cargo-tree>

<https://github.com/uutils/coreutils>

<https://github.com/bootandy/dust>

<https://github.com/conky5/eq>

<https://github.com/Edu4rdSHL/findomain>

<https://github.com/sitkevij/hex>

<https://github.com/sharkdp/hyperfine>

<https://github.com/ilai-deutel/kibi>

<https://github.com/raftario/licensor>

<https://github.com/rust-lang/mdBook>

<https://github.com/meilisearch/MeiliSearch>

<https://github.com/svenstaro/miniserve>

<https://github.com/Y2Z/monolith>

<https://github.com/nushell/nushell>

<https://github.com/dalance/procs>

<https://github.com/phra/rustbuster>

<https://github.com/lotabout/skim>

<https://github.com/nelsonjchen/speedtest-rs>

<https://github.com/starship/starship>

<https://github.com/endgameinc/xori>

<https://github.com/yewstack/yew>

<https://github.com/cjbassi/ytop>

<https://github.com/bvaisvil/zenith>

<https://github.com/ajeetdsouza/zoxide>
