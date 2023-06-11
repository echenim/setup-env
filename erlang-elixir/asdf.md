brew install asdf

Install Plugins
ASDF uses a plugin system to support multiple languages. For a typical Elixir project, you will need the Elixir and Erlang plugins:

asdf plugin add erlang
asdf plugin add elixir
shell
If your project requires Node.js, you can also install the nodejs plugin.

Install Erlang/OTP
With ASDF and its plugins installed, you can now install Elixir and Erlang. If your project has a .tool-versions file with entries for elixir and erlang, you can install the correct versions by running the following from inside the project:

asdf install
shell
The .tool-versions file is much like .nvmrc and .ruby-version files, except that it lists the names and versions of multiple languages. In general, the names in this file should match the names of the language's plugin (e.g. nodejs for Node.js).

If you do not yet have a .tool-versions file, or want to install Elixir and Erlang globally, use the following to see a list of all available Erlang/OTP versions:

asdf list-all erlang

#

23.2
23.2.1
23.2.2

#

shell
Unlike other version managers, ASDF requires you to specify a precise version of the language to install. To install version 23.2.1 of Erlang, run:

asdf install erlang 23.2.1
shell
Warning: This installation will take some time while it compiles Erlang from source.

Erlang will compile modules based on the available libraries from your system. For example, some features (such as the built-in observer) require wx libraries. You may see messages during the installation about omitted modules, which will not affect the rest of the runtime.


Install Elixir
Once the Erlang runtime is installed, you are ready to install Elixir. To see a list of all available versions, run:

asdf list-all elixir

#

1.11.2
1.11.2-otp-21
1.11.2-otp-22
1.11.2-otp-23

#

shell
Notice that each Elixir release has multiple versions compiled with different major versions of Erlang/OTP. To maximize compatibility between Elixir and the Erlang runtime, choose a -otp-XY version that matches the major version of the runtime you installed in the previous step. For example:

asdf install elixir 1.11.2-otp-23
shell
Installing Elixir takes significantly less time than installing Erlang/OTP.
Set Versions
Now that you have Elixir and Erlang/OTP installed, you can save your chosen versions in a project. From the root of the project, run:

asdf local erlang 23.2.1
asdf local elixir 1.11.2-otp-23
shell
Replace the versions above with those you used during installation. This will create a .tool-versions file in your project, which will instruct ASDF which versions to use. If you'd like to set a global, or default, version, run:

asdf global erlang 23.2.1
asdf global elixir 1.11.2-otp-23
shell
This will create a .tool-versions file in your home directory. ASDF will use these versions whenever a project doesn't specify versions of its own.
