---
layout: post
title:  "rbenv - Ruby Version Control"
date:   2023-11-06 09:40:14 +0400
categories: ruby programming 
permalink: "/:title" 
---
It's often easier to manage your Ruby installations with a Ruby version manager like `rbenv` or `rvm`. These tools allow you to install Ruby in your home directory, thus avoiding the need for `sudo`.

I decided to go with `rbenv`:

In your terminal (bash/zsh)

```bash
# Install rbenv 
brew install rbenv

# Initialize rbenv 
rbenv init

# Install a Ruby version - replace the XX with whatever version you want to install
rbenv install 3.XX.XX

# Set the Ruby version for your session or globally - replace the XX with whatever version you want to make global
rbenv global 3.XX.XX

# Now install Rails 
gem install rails
```


If you've installed Ruby using `rbenv` but your system still points to the default Ruby installation when you run `which ruby`, you need to ensure `rbenv` is properly configured in your shell. Here's how you can do that:

1. **Initialize rbenv**

   Ensure that `rbenv` is properly initialized by adding the following to your shell configuration file (`.bashrc`, `.zshrc`, etc.):

   ```sh
   export PATH="$HOME/.rbenv/bin:$PATH"
   eval "$(rbenv init -)"
   ```

   After adding the above lines, you'll need to restart your terminal or source your configuration file with:

   ```sh
   source ~/.bashrc        # If you are using bash
   source ~/.zshrc         # If you are using zsh
   ```

2. **Set the global Ruby version**

   After initializing `rbenv`, set the global Ruby version to the one you've installed:

   ```sh
   rbenv global <version>
   ```

   Replace `<version>` with the version number that you installed with `rbenv`.

3. **Verify the change**

   After setting the global version, verify that `rbenv` is pointing to the correct Ruby version:

   ```sh
   rbenv versions  # This will show all installed Ruby versions and highlight the global one.
   ```

   Then check again using:

   ```sh
   which ruby
   ```

   It should now point to the Ruby installation managed by `rbenv`, typically located in `~/.rbenv/shims/ruby`.

4. **Rehash rbenv**

   Whenever you install a new version of Ruby or a gem that provides commands, you should run:

   ```sh
   rbenv rehash
   ```

   This command sets up shims for all Ruby executables known to `rbenv`, which allows `rbenv` to manage your Ruby binaries.

5. **Local Version (Optional)**

   If you want to set Ruby version for a specific project, navigate to the project directory in the terminal and run:

   ```sh
   rbenv local <version>
   ```

   This will create a `.ruby-version` file in your project directory, and any time you work within that directory, `rbenv` will use the version specified.

