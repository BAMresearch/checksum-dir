# Manage checksums for a directory structure

Developed and tested for Linux.

## Usage

Run `checksum-dir [<path to create checksums for> | <checksum file>]`

1. Calculates checksums of all files in the given path recursively.
   The checksums are stored with relative paths in a file
   'check_\<datetimestamp\>.sha256' in the given directory.
2. When verifying checksums, it works with relative paths based on
   the checksum file location and absolute paths.

Change to the directory to checksum and run the script there ('$' indicates the shell prompt, it's not part of the command):

    $ cd .dawn/
    $ checksum-dir .
    Creating '/home/ingo/.dawn/check_250206144142.sha256':
    64c53a48d36274e052885fb4d8c04f51e3f45edda6d08d596b3aa23b4f666537 *./org.eclipse.osgi/.manager/.fileTable.2
    d5ee4cb634e5381df0678d0e6628e82c7915b8c508b307f0864ff42b23502f64 *./org.eclipse.osgi/.manager/.fileTable.1
    5901e6933874c7b8f3ff032eefb0f7ead8c0794eb7135d74d3b4413eb170d9d4 *./org.eclipse.osgi/framework.info.1
    4c2fddf5208b747d0a1a4c808efc1fa662a57751f3c589ab6e9fe238ca6c730d *./org.eclipse.core.runtime/.table.1
    b0912c3816220a45077e651f4b18f477f562a262be4e67719582338389edb3d8 *./org.eclipse.core.runtime/.manager/.fileTable.8
    00810eba738b4ff11f442b6e6de9ca5714b8f13d789b04633b4590938410ca55 *./org.eclipse.core.runtime/.manager/.fileTable.7
    a346de00c1e4d756dddab897fa58c83859fe58bc964b8119160e0ee20df3218d *./org.eclipse.core.runtime/.extraData.1
    7a3c8416f5442595a3d470336eaa95d01336867ac390f1225b7af905a204bcd0 *./org.eclipse.core.runtime/.contributions.1
    b65e15a186b2f3450a2ade3ac0f223483ca696d87668f09c9837dc54b53ff82a *./org.eclipse.core.runtime/.namespaces.1
    d70677954e00d5256809e003a3f08842feb233a6e9e43899c3a2afe105437f51 *./org.eclipse.core.runtime/.mainData.1
    c1c29e104bb2102ae714bbdd68c1171682ec31beb0fae136c04c3c78abbef9bc *./org.eclipse.core.runtime/.contributors.1
    96a19174d3246c958053b5eb62ab594350cfba7ba97553e1f7a528744bd1a051 *./org.eclipse.core.runtime/.orphans.1
    a2f678a4f4fd38ff2afd483ed9227f7f86f7f71fb979979965d2c666db0f7bc9 *./config.ini
    526b190306b08b9869c458d20d8f258913686319f1ab5871866cc20ecf015374 *./org.eclipse.update/platform.xml
    $ ls -la
    total 32K
    drwxrwx---  6 ingo ingo 4,0K Feb  6 14:41 .
    drwxr-x--- 28 ingo ingo 4,0K Feb  6 14:19 ..
    -rw-rw-r--  1 ingo ingo 1,5K Feb  6 14:41 check_250206144142.sha256
    -rw-rw----  1 ingo ingo  104 Jul 28  2022 config.ini
    drwxrwx---  3 ingo ingo 4,0K Jul 28  2022 org.eclipse.core.runtime
    drwxrwx---  3 ingo ingo 4,0K Jul 28  2022 org.eclipse.equinox.app
    drwxrwx---  3 ingo ingo 4,0K Jul 28  2022 org.eclipse.osgi
    drwxrwx---  2 ingo ingo 4,0K Jul 28  2022 org.eclipse.update

Check the directory and all its files by calling the script with the checksum file as argument from anywhere:

    $ cd /
    $ checksum-dir ~/.dawn/check_250206144142.sha256
    Verifying checksums from '/home/ingo/.dawn/check_250206144142.sha256':
    All good!

If there was an error:

    $ checksum-dir ~/.dawn/check_250206144142.sha256
    Verifying checksums from '/home/ingo/.dawn/check_250206144142.sha256':
    ./org.eclipse.core.runtime/.extraData.1: FAILED
    sha256sum: WARNING: 1 computed checksum did NOT match

## Install (on Linux)

Clone this repo first, to get the file:

    cd $HOME
    mkdir -p code && cd code # or another source code directory
    git clone https://github.com/BAMresearch/checksum-dir.git

Link to the script in a directory which is in your $PATH,
 `/usr/local/bin` for system-wide availablity here:

    cd /usr/local/bin
    sudo ln -s $HOME/code/checksum-dir/checksum-dir .
