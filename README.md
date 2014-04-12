android_local_normandy
======================

Local Manifest for CAF/AOSP Jellybean 4.1.2 on Nokia X (normandy)

Getting Started
---------------

To get started with Android, you'll need to get
familiar with [Git and Repo](http://source.android.com/download/using-repo).

Make a build directory:

	mkdir Andoid (or whatever name you choose, which will be refered to as Android throughout)
	cd Android
	mkdir .repo/local_manifests

To initialize your local repository using the CAF manifest, use commands like these:

    repo init -u git://codeaurora.org/platform/manifest.git -b release -m M8625QSOSKMLYA31201C.xml

    curl -L -o .repo/local_manifests/caf_msm8625.xml -O -L https://raw.github.com/dhacker29/android_local_normandy/caf_jb_rel_2.0.3/caf_msm8625.xml
 
    	( or Download: https://github.com/dhacker29/android_local_normandy/blob/caf_jb_rel_2.0.3/caf_msm8625.xml
		and place it in ~/Android/.repo/local_manifest.xml

Then to sync up:

    repo sync

You will need to apply some pathces to fix build erros and other bugs:

    cd Android/device/nokia/normandy/patches
    ./apply.sh

To build issue commands like these:

    cd Android
    . build/envsetup.sh && lunch msm8625-userdebug
    make -jX otapackage (where X equals twice the number of cpu cores +1)
