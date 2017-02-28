---
layout: git-post
date: 2017-02-28 09:12:45 +0100
title: "Releasing"
categories: git howto repository
tags: tag describe archive
level: expert
permalink: /git/expert/releasing
---

Your project is in a stable state and you want to create a release? Let's do it!

### First step: create a signature

You need to have a signature to nicely create a release and signature are stored with gpg. To know the currently stored signatures, run

    $ gpg --list-keys

If nothing appears or if you can't find your email in the output, you must create your signature with:

    $ gpg --gen-key
    Please select what kind of key you want:
    (1) RSA and RSA (default)
    (2) DSA and Elgamal
    (3) DSA (sign only)
    (4) RSA (sign only)
    Your selection? 

Chose `1` to create an asymetric signature

    RSA keys may be between 1024 and 4096 bits long.
    What keysize do you want? (2048)

Default is fine, hit `<Return>`

    Please specify how long the key should be valid.
    0 = key does not expire
    d = key expires in n days
    w = key expires in n weeks
    m = key expires in n months
    y = key expires in n years
    key is valid for? (0) 

It is a nice idea to set a expiration date. And there is a way to change it, so say `1y`

    Key expires at <date>
    Is this correct? (y/N)

Should be `y`
    
    You need a user ID to identify your key; the software constructs the user ID
    from the Real Name, Comment and Email Address in this form:
        "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

    Real name: <your name>
    Email address: <your email>
    Comment: <message>
    You selected this USER-ID:
        "<your name> (<message>) <<your email>>"

    Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?

Check entered datas, then `O`.

    You need a Passphrase to protect your secret key.

    Enter passphrase: <passphrase>
    Repeat passphrase: <passphrase>
    
    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    ....+++++
    +++++
    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    ..............+++++
    .....+++++
    gpg: key <pub_hash> marked as ultimately trusted
    public and secret key created and signed.

    gpg: checking the trustdb
    gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
    gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
    gpg: next trustdb check due at 2018-02-28
    pub   2048R/<pub_hash> 2017-02-28 [expires: 2018-02-28]
          Key fingerprint = <fingerprint>
    uid                  <your name> (<message>) <<your email>>
    sub   2048R/<sub_hash> 2017-02-28 [expires: 2018-02-28]

    $

Now check gpg:

    $ gpg --list-keys
    <gpg file>
    ------------------------------------
    pub   2048R/<pub_hash> 2017-02-28 [expires: 2018-02-28]
    uid                  <your name> (<message>) <<your email>>
    sub   2048R/<sub_hash> 2017-02-28 [expires: 2018-02-28]

Allright, gpg is configured.

### Share public signature with git

Signing release tags allows end users / contributors to verify release tags, but they need your public key. Here is a way to publish it.  
First, add your public key to a git blob object:

    $ gpg -a --export <pub_hash> | git hash-object -w --stdin
    <git_key_hash>

Then, tag this object:

    $ git tag -a maintainer-gpg-pub <git_key_hash> -m "Public gpg maintainer key"
    $ git push --tags

Now your public key is shared to anyone who wants to verify a tag.

### Create a signed tag

Now you can create a signed tag. But create just one tag by release, no need to create one for each release build. I'll explain why later in this post.

    $ git tag -s <tagname> -m "<message>"
   
    You need a passphrase to unlock the secret key for
    user: "<your name> (<message>) <<your email>>"
    2048-bit RSA key, ID <pub_hash>, created 2017-02-28
    
    Enter passphrase:

It is possible you have an error here:

    $ git tag -s <tagname> -m "<message>"
    gpg: skipped "<wrong name> <<wrong email>>": secret key not available
    gpg: signing failed: secret key not available
    error: gpg failed to sign the data
    error: unable to sign the tag

In this case, you must use:

    git tag -u <sub_hash> <tagname> -m "<message>"

    You need a passphrase to unlock the secret key for
    user: "<your name> (<message>) <<your email>>"
    2048-bit RSA key, ID <pub_hash>, created 2017-02-28
    
    Enter passphrase:


### Verify a tag


### Generate a build number

This command will generate for you a *build* number, not a *release* number. The release number is in fact the tag name!  
Here is the format of the generated build number: `<tagname>-<nb>-<hash>` where `<tagname>` is the last annotated tag name (and signed tags are annotated), `<nb>` the number of commits since the tag and `<hash>` the abbreviate used commit hash. If the last signed tag is at `HEAD`, `<nb>` and `<hash>` are ommitted.  
How to generate this number?

    $ git describe <object>
    <tagname>-<nb>-<hash>

`<object>` can be `master`, `<branch-name>`, `<tag-name>`, `<commit-hash>`, `HEAD`, `HEAD^`, ... or nothing (which means `HEAD`).

You also can specific the size of abbreviate hash using the `--abbrev=<n>` option, where `<n>` is the size of the abbreviate hash. For example, the Linux kernel project is currently using `--abbrev=10`.

The output is not usable only for creating a release. You can use it as `<object>` for commands like `checkout` or `show`.

### Build a release

Now it's time to build your release. You can create a tarball and/or a zip archive of a specific snapshot:

    $ git archive <object> | gzip > `git describe <object>`.tar.gz      # tarball
    $ git archive <object> --format=zip > `git describe <object>`.zip   # zip

where `<object>` can took the same values than for `describe` except that you must specify `HEAD` instead of nothing.

If you look into your project directory, you should show a 'tar.gz' and a 'zip' archives with the same name. This is the archives you just created!

You maybe want to only put the files from a subfolder in archives. It is possible with the `--prefix` option:

    $ git archive <object> --prefix='<path>/' | gzip > `git describe <object>`.tar.gz      # tarball
    $ git archive <object> --prefix='<path>/' --format=zip > `git describe <object>`.zip   # zip

or put the archives in a specific folder:

    $ git archive <object> | gzip > path/to/`git describe <object>`.tar.gz      # tarball
    $ git archive <object> --format=zip > path/to/`git describe <object>`.zip   # zip

I suggest you to create two aliases for `archive`, commands are long:

    $ git config --global alias.arc_tar 'archive master | gzip > releases/`git describe master`.tar.gz'
    $ git config --global alias.arc_zip 'archive master --format=zip > releases/`git describe master`.zip'

or create a script like this one (named `git-arc.sh`) in your working directory and run it:

```
#!/bin/sh

function usage
{
    echo "NAME"
    echo "git-arc: optionnaly tag, create tarball and zip release archives"
    echo ""
    echo "SYNOPSIS"
    echo "git-arc [-t tagname [-m message]] [what]"
    echo ""
    echo "OPTIONS"
    echo "  -t <tagname>"
    echo "    The tag name (optionnal). Tag will be create at 'what'"
    echo ""
    echo "  -m <message>"
    echo "    The message associate to the tag (optionnal). Default is \"release tag\""
    echo ""
    echo "  what"
    echo "    Position to create the tag and make archives. Can be 'master', '<commit_hash>', 'HEAD', 'HEAD^', ... Default is 'HEAD'"
}

tagname="no"
message="release tag"
what="HEAD"

# getting parameters
while [[ $1 ]]; do
    case $1 in 
        -t)                 shift
                            tagname=$1
                            ;;
        -m)                 shift
                            message=$1
                            ;;
        -h | --help)        usage
                            exit 0
                            ;;
        * )                 what=$1
                            ;;
    esac
    shift
done

# check if "releases" directory exists
if [ -d "releases/" ]; then
    mkdir releases
fi

# must create tag?
if [ "$tagname" != "no" ]; then
    echo "Create '"$tagname"' tag..."
    git tag -s $tagname $what -m "${message}"
    if [ $? != 0 ]; then
        echo "Error while creating tag"
        exit 1
    fi
fi

build=$(git describe $what)

echo "Building archives for "$build"..."
# tarball
git archive ${what} | gzip > releases/${build}.tar.gz
if [ $? != 0 ]; then
    echo "Error while creating tar.gz archive"
    exit 1
fi

# zip
git archive ${what} --format=zip > releases/${build}.zip
if [ $? != 0 ]; then
    echo "Error while creating zip archive"
    exit 1
fi

echo "Done"
exit 0
```

and run it into your working directory.
