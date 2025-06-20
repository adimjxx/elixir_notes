>**Kerl** allows you to easily build and switch between different Erlang versions. Install Kerl and build & install an OTP version first, as Kiex needs Erlang to be present.
---
>**Kiex** allows you to easily build and switch between different [Elixir](http://elixir-lang.org/) versions. 
>
>It supports setting the default (global) Elixir version as well as per shell/project versions.
>
>Everything is self-contained under ~/.kiex.

Usage is based _lightly_ on [RVM](http://rvm.io/), [kerl](https://github.com/spawngrid/kerl), and [rbenv](https://github.com/sstephenson/rbenv).

1. Setup kerl:
```bash
curl -O https://raw.githubusercontent.com/kerl/kerl/master/kerl
```

```bash
╰─ ./kerl list releases all
Getting releases from GitHub...
R13B03
R13B04
R14A
R14B
R14B01
R14B02
.
.
.
28.0-rc4
28.0
Run './kerl update releases' to update this list

╰─ ./kerl build 28.0
Downloading (from GitHub) Erlang/OTP 28.0 to /home/d3v/.kerl/archives...
Extracting source code for normal build...
Building (normal) Erlang/OTP 28.0 (28.0); please wait...
Initializing (build) log file at /home/d3v/.kerl/builds/28.0/otp_build_28.0.log.
autoconf: error: no input file
APPLICATIONS DISABLED (See: /home/d3v/.kerl/builds/28.0/otp_build_28.0.log)
 * odbc           : ODBC library - link check failed

APPLICATIONS INFORMATION (See: /home/d3v/.kerl/builds/28.0/otp_build_28.0.log)
 * wx             : wxWidgets was not compiled with --enable-webview or wxWebView developer package is not installed, wxWebView will NOT be available

Erlang/OTP 28.0 (28.0) has been successfully built.`
```

2. Install the build:
```bash
╰─ ./kerl install 28.0 erl_28_0
Installing Erlang/OTP 28.0 (28.0) in /home/d3v/.kerl/erl_28_0...
Initializing (install) log file at /home/d3v/.kerl/builds/28.0/otp_install_28.0.log.
You can activate this installation running the following command:
. /home/d3v/.kerl/erl_28_0/activate
Later on, you can leave the installation typing:
kerl_deactivate
```

3. Activate/deactivate the Erlang install using the following commands
```bash
. /home/$USER/.kerl/erl_28_0/activate
kerl_deactivate
```
Or you can add a `source` line to your `rc` file.

4. Setup [kiex](https://github.com/taylor/kiex)
```bash
\curl -sSL https://raw.githubusercontent.com/taylor/kiex/master/install | zsh -s
```

```bash
╰─ \curl -sSL https://raw.githubusercontent.com/taylor/kiex/master/install | zsh -s
Running initial environment setup
    Kiex sourcing line not found in ~/.bashrc, ~/.bash_profile, ~/.profile, ~/.zshrc, or ~/.zsh_profile
    Add the following to your shell's config file (.bashrc/.zshrc/.cshrc):
        test -s "$KIEX_HOME/scripts/kiex" && source "$KIEX_HOME/scripts/kiex"
kiex has been installed in /home/d3v/.kiex ☺
```
After adding the suggested line to your `rc` file (which is for the Elixir tools), make sure to add `kiex` to `PATH`.
```bash
# add the following in your `rc` file
export PATH=$PATH:/home/d3v/.kiex/bin
```

5. Install a kiex elixir
```bash
╰─ kiex list known
Getting the available releases from https://github.com/elixir-lang/elixir/releases

Known Elixir releases:
    main-latest
    1.5.0
    1.5.0-rc.1
    1.5.0-rc.2
    1.5.1
    .
    .
    .
    1.18-latest
    1.18.1
    1.18.2
    1.18.3
    1.18.4
    1.19.0-rc.0
    1.19-latest
```

```bash
╰─ kiex install 1.19-latest
Downloading elixir version 1.19-latest
Installing elixir version 1.19-latest into /home/d3v/.kiex/elixirs/elixir-1.19-latest-28
error: pathspec 'master' did not match any file(s) known to git
Switched to a new branch 'v1.19-latest'
From https://github.com/elixir-lang/elixir
 * tag                   v1.19-latest -> FETCH_HEAD
Already up to date.
rm -f man/elixir.1
rm -f man/elixir.1.bak
rm -f man/iex.1
rm -f man/iex.1.bak
rm -rf ebin
rm -rf lib/*/ebin
rm -rf lib/elixir/src/elixir_parser.erl
rm -rf lib/*/_build/
rm -rf lib/*/tmp/
rm -rf lib/elixir/test/ebin/
rm -rf lib/mix/test/fixtures/deps_on_git_repo/
rm -rf lib/mix/test/fixtures/git_rebar/
rm -rf lib/mix/test/fixtures/git_repo/
rm -rf lib/mix/test/fixtures/git_sparse_repo/
rm -rf lib/mix/test/fixtures/archive/ebin/
rm -f erl_crash.dump
rm -rf cover
Recompile: src/iex
Recompile: src/elixir_utils
Recompile: src/elixir_tokenizer
Recompile: src/elixir_sup
Recompile: src/elixir_rewrite
Recompile: src/elixir_quote
Recompile: src/elixir_parser
Recompile: src/elixir_overridable
Recompile: src/elixir_module
Recompile: src/elixir_map
Recompile: src/elixir_lexical
Recompile: src/elixir_json
Recompile: src/elixir_interpolation
Recompile: src/elixir_import
Recompile: src/elixir_fn
Recompile: src/elixir_expand
Recompile: src/elixir_errors
Recompile: src/elixir_erl_var
Recompile: src/elixir_erl_try
Recompile: src/elixir_erl_pass
Recompile: src/elixir_erl_for
Recompile: src/elixir_erl_compiler
Recompile: src/elixir_erl_clauses
Recompile: src/elixir_erl
Recompile: src/elixir_env
Recompile: src/elixir_dispatch
Recompile: src/elixir_def
Recompile: src/elixir_config
Recompile: src/elixir_compiler
Recompile: src/elixir_code_server
Recompile: src/elixir_clauses
Recompile: src/elixir_bootstrap
Recompile: src/elixir_bitstring
Recompile: src/elixir_aliases
Recompile: src/elixir
Generated elixir app
==> bootstrap (compile)
Compiled kernel.ex
Compiled kernel/utils.ex
Compiled macro/env.ex
Compiled range.ex
Compiled keyword.ex
Compiled module.ex
Compiled list.ex
Compiled macro.ex
Compiled kernel/typespec.ex
Compiled code.ex
Compiled code/identifier.ex
Compiled protocol.ex
Compiled stream/reducers.ex
Compiled enum.ex
Compiled regex.ex
Compiled inspect/algebra.ex
Compiled inspect.ex
Compiled string.ex
Compiled string/chars.ex
Compiled kernel.ex
Compiled list/chars.ex
Compiled bitwise.ex
Compiled module/parallel_checker.ex
Compiled module/behaviour.ex
Compiled module/types/helpers.ex
Compiled module/types/descr.ex
Compiled module/types/of.ex
Compiled module/types/pattern.ex
Compiled module/types/apply.ex
Compiled module/types/expr.ex
Compiled module/types.ex
Compiled exception.ex
Compiled path.ex
Compiled file.ex
Compiled map.ex
Compiled access.ex
Compiled io.ex
Compiled system.ex
Compiled code/formatter.ex
Compiled code/normalizer.ex
Compiled kernel/cli.ex
Compiled kernel/error_handler.ex
Compiled kernel/parallel_compiler.ex
Compiled kernel/lexical_tracker.ex
make[1]: Entering directory '/home/d3v/.kiex/builds/elixir-git'
==> unicode (compile)
[Unicode] Break on 25 whitespace codepoints
[Unicode] Tokenizing 112700 non-ascii codepoints
[Unicode] Tokenizing 65 scriptsets
make[1]: Leaving directory '/home/d3v/.kiex/builds/elixir-git'
==> elixir (compile)
Generated elixir app
==> eex (compile)
==> mix (compile)
Generated mix app
==> ex_unit (compile)
Generated ex_unit app
==> logger (compile)
Generated logger app
Generated eex app
==> iex (compile)
Generated iex app
==> elixir (install)
"make" install_man
make[1]: Entering directory '/home/d3v/.kiex/builds/elixir-git'
"make" clean_man
make[2]: Entering directory '/home/d3v/.kiex/builds/elixir-git'
rm -f man/elixir.1
rm -f man/elixir.1.bak
rm -f man/iex.1
rm -f man/iex.1.bak
make[2]: Leaving directory '/home/d3v/.kiex/builds/elixir-git'
make[1]: Leaving directory '/home/d3v/.kiex/builds/elixir-git'
Installed Elixir version 1.19-latest
Load with:
           kiex use 1.19-latest-28
or load the elixir environment file with:
   source /home/d3v/.kiex/elixirs/elixir-1.19-latest-28.env
```
# Resource mods
```bash
# elixir
source /home/d3v/.kerl/erl_27_3_4/activate
export PATH=$PATH:/home/d3v/.kiex/bin
source /home/d3v/.kiex/elixirs/elixir-1.17.3-27.env
```