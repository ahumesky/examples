# Android NDK with Bazel example

## Documentation

For the full documentation, please visit the [Bazel documentation page](https://bazel.build/docs/android-ndk).

## Instructions

1) Launch emulator
2) Run `bazel mobile-install //app/src/main:app --android_platforms=//:x86 --start_app`

<img src="images/result.png" width="400px" />

## Build graph

![](/images/graph.png)

- JNI/C++ sources goes into the `cc_library` target, `//app/src/main:jni_lib`.
- Java sources, resource files, and assets go into the `android_library`
  target, `//app/src/main:lib`. This target depends on the `cc_library` target.
- The APK is built from the `android_binary` target, `//app/src/main:app`. This
  target depends on the `android_library` target.

NOTE: This graph omits the Google Maven AAR dependencies.
