# APT

 Installing Software (Historically)

    Download source code

    Compile (C code → GCC), or save as script (Bash)

    Modern systems use package managers

⚙️ Compiling & Dependencies

    Source code defines required dependencies

    If any are missing, compile fails

    Dependencies = shared libraries for modular code

    Ex: MD5 hashing via a library instead of writing your own

🔄 Dependency Scenarios

    Multiple Versions:
    App1 needs libfoo v1.2, App2 needs v1.3 → version conflict

    Nested Dependencies:
    Libraries may depend on many sub-libraries → complex chains

    Circular Dependencies:
    AppX v1 → app2 → app3 → app4 → AppX v0 → requires installing all versions simultaneously

📦 Packages

A package includes:

    Scripts, binaries, files, directories, dependency list

    Can be executables or source code

📚 Package Management System (PMS)

Handles:

    Install / Upgrade / Remove / Search

    Based on a local database synced with remote repositories

🌐 Repositories

    Hosts packages for a specific Linux distribution

    Sources: Internet, internal server, DVD

    Format defined per distro

    Debian repos listed in /etc/apt/sources.list
    Example:
    deb http://deb.debian.org/debian bullseye-updates main

📦 Package Formats

    .deb → Debian/Ubuntu

    .rpm → Red Hat/CentOS

    .tar.gz → Source code

🧰 dpkg (Debian Package Manager)

    Installs .deb files manually

    Does not auto-install dependencies

    Doesn’t connect to repos

Key dpkg Commands:

dpkg -i file.deb            # Install
dpkg -r tmux                # Remove
dpkg-query --list           # List all
dpkg-query --list tmux      # Query tmux

🔧 apt (Advanced Package Tool)

    Front-end for dpkg

    Handles dependencies automatically

    Connects to repositories

List Commands:

apt list --installed
apt list --upgradeable
apt list --all-versions tmux
apt list --installed tmux

Install/Search/Info:

apt install tmux
apt search tmux
apt-file search bin/tmux     # Requires `apt-file` package
apt info tmux

Updates:

apt update     # Refresh repo list
apt upgrade    # Upgrade installed packages

❓ Why Use dpkg?

    Repo versions are stable but sometimes outdated

    For newer features, download .deb manually and install with dpkg

    Be ready to manage dependencies yourself

🔍 .deb File Breakdown

Example: nano-2.2.6-1.i386.deb

    nano = name

    2.2.6 = version

    -1 = release (security/backport)

    i386 = 32-bit (others: i486, i586, i686, amd64 = 64-bit)

➕ Adding Repos

    You can manually add repositories

    Only trust known sources

    Examples:

        Node.js: https://github.com/nodesource/distributions

        Docker: https://docs.docker.com/engine/install/debian/

🧩 Other Package Formats

    FlatPak (Red Hat): https://flatpak.org/

    Snap (Canonical): https://snapcraft.io/

    AppImage (Community): https://appimage.org/
