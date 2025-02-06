# Manage checksums for a directory structure

Developed and tested for Linux.

## Install (on Linux)

Clone this repo first, to get the file:

    cd $HOME
    mkdir -p code && cd code # or another source code directory
    git clone https://github.com/BAMresearch/checksum-dir.git

Link to the script in a directory which is in your $PATH,
 `/usr/local/bin` for system-wide availablity here:

    cd /usr/local/bin
    sudo ln -s $HOME/code/checksum-dir/checksum-dir .

