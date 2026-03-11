# june-xu.github.io
Learn about me! 


blog

---

## Building locally

### One-time setup

1. **Install Bundler** (version locked in `Gemfile.lock`):
   ```bash
   gem install bundler:2.2.13 --user-install
   ```
   Add your user gem bin to `PATH` (e.g. in `~/.zshrc`):
   ```bash
   export PATH="$HOME/.gem/ruby/2.6.0/bin:$PATH"
   ```

2. **Install gems into the project** (no sudo):
   ```bash
   cd /path/to/june-xu.github.io
   bundle config set --local path 'vendor/bundle'
   bundle install
   ```

### Build and serve

```bash
bundle exec jekyll build   # one-off build → output in _site/
bundle exec jekyll serve  # build + serve at http://localhost:4000
```

**Apple Silicon (M1/M2/M3):** If you see an error like `mach-o file, but is an incompatible architecture (have 'x86_64', need 'arm64')`, install native gems with:

```bash
bundle lock --add-platform arm64-darwin
bundle install
```

**If the build crashes** with a Bus Error in `sassc`/FFI (older setups): this project uses Jekyll 4.3+ with Dart Sass (`sass-embedded`) instead of `sassc`, which avoids that crash. If you still hit issues, use Ruby 3.x (e.g. `rbenv install 3.2.0` and `rbenv local 3.2.0`), then `bundle install` and build again.

Otherwise you can rely on GitHub Pages to build the site when you push.
