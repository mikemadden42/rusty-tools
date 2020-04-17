# rusty-tools

## Resources

<https://discussion.fedoraproject.org/t/tools-applications-written-in-rust/1040>

<https://fedoramagazine.org/oxidizing-fedora-try-rust-applications-today/>

<https://www.reddit.com/r/rust/comments/cap9ul/debian_10_released_contains_ripgrep_fdfind_exa/>

<https://www.debian.org/releases/stable/amd64/release-notes/ch-whats-new.en.html#newdistro>

<https://msrc-blog.microsoft.com/2019/11/07/using-rust-in-windows/>

<https://barcelona.rustfest.eu/sessions/r-evolution>

<https://www.zdnet.com/article/microsoft-opens-up-rust-inspired-project-verona-programming-language-on-github/>

## Tools

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

bat -A /etc/hosts

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

exa -1

exa -a

exa -l -snew
```

## fd

```bash
fd -h

cd ~/src/mikemadden42
fd linpack

fd passwd /etc

cd
fd . src/mikemadden42/beats-tester

cd ~/src/mikemadden42/beats-tester
fd -e yml

# https://en.wikipedia.org/wiki/.DS_Store
fd -H '^\.DS_Store$' -tf
fd -H '^\.DS_Store$' -tf -X rm
```

## ffsend

```bash
ffsend -h

ffsend upload cat.jpg

ffsend exists URL

ffsend info URL

ffsend delete URL

ffsend password URL

ffsend download URL
```

## hexyl

```bash
hexyl -h

hexyl -n 256 cat.jpg
```

## lsd

<https://github.com/Peltoche/lsd/issues/199#issuecomment-494218334>

```bash
lsd --help

lsd -1

lsd -a

lsd -l

lsd -lh

lsd -lht

lsd -lhrt
```

## rage

```bash
rage -h

rage -p -o cat.jpg.age cat.jpg

rage -d -p cat.jpg.age > cat2.jpg

gsha1sum cat*.jpg

rage -p -a -o cat2.jpg.age cat.jpg

bat cat2.jpg.age
```

## rg

```bash
rg -h
```

Recursively searching your current working directory is the default mode of operation for ripgrep.
This repo has 15+ millions lines of code and comments.  rg finds results in under a couple seconds.

```bash
cd ~/src/mikemadden42/endpoint-dev
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

sed -i 's/1.13.5/1.13.6/g' README.md

sd 1.13.5 1.13.6 README.md
sd 1.13.5 1.13.6 go1.13/Makefile.common
sd 1.13.5 1.13.6 go1.13/base/Dockerfile.tmpl
sd 512103d7ad296467814a6e3f635631bd35574cab3369a97a323c9a585ccaa569 a1bc06deb070155c4f67c579f896a45eeda5a8fa54f35ba233304074c4abbbbd go1.13/base/Dockerfile.tmpl
```

## tokei

<https://github.com/AlDanial/cloc>

<https://dwheeler.com/sloccount/>

<https://github.com/hhatto/gocloc>

<https://github.com/boyter/scc>

```bash
tokei -h

tokei -l

cd ~/go/src/github.com/elastic/beats

tokei

tokei -slines .

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

<https://github.com/endgameinc/xori>

<https://github.com/yewstack/yew>

<https://github.com/cjbassi/ytop>

<https://github.com/bvaisvil/zenith>

<https://github.com/ajeetdsouza/zoxide>
