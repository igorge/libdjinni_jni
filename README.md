libdjinni_jni
====
djinni support lib.

Add via "git submodule add https://github.com/igorge/libdjinni_jni modules/djinni_jni"
Init via "git submodule update --init && git submodule foreach git checkout master"
Update via "git submodule update --remote --merge"

Add "${djinni_jni_SOURCE_DIR}/src/support-lib/jni/djinni_main.cpp" to sources for default JNI_OnLoad/JNI_OnUnload.
