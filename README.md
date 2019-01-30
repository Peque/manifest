Docker environment
------------------

Follow the instructions at [stucki/docker-lineageos](https://github.com/stucki/docker-lineageos) to setup your LineageOS build environment.

Run your environment with the script:

```
./run.sh
```


Preparation
-----------

Make sure you have `git` configured:

```
git config --global user.email "foo@bar.com"
git config --global user.name "Foo Bar"
```

Initialize your local LineageOS repository:

```
repo init -u git://github.com/LineageOS/android.git -b lineage-15.1
```

Now create a local manifest:

```
mkdir -p .repo/local_manifests
wget -O .repo/local_manifests/moto8916.xml https://raw.githubusercontent.com/Peque/manifest/lineage-15.1/moto8916.xml'
```


Building
--------

Sync:

```
repo sync -c -f --force-sync -j16
```

Or, if you would rather do a fast sync and build:

```
repo sync --current-branch --no-tags --no-clone-bundle --optimized-fetch --force-broken --force-sync -j16
```

Setup the environment:

```
source build/envsetup.sh
```

And, finally, build:

```
breakfast <devicecodename>
brunch <devicecodename>
```
