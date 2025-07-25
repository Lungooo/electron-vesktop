# Maintainer: Sophie Langer <sophie@lungoo.dev>

# https://releases.electronjs.org/
# https://gitlab.com/Matt.Jolly/chromium-patches/-/tags

# Note: source array can be synced with an Electron release after updating $pkgver with:
# bash -c 'source PKGBUILD; _update_sources'

pkgver=37.2.1
_gcc_patches=138-1
pkgrel=1
_major_ver=${pkgver%%.*}
pkgname="electron-vesktop"
pkgdesc='Build cross platform desktop apps with web technologies (Vesktop patched)'
arch=(x86_64)
url='https://electronjs.org'
license=(MIT BSD-3-Clause)
depends=(c-ares
         gcc-libs # libgcc_s.so
         glibc # libc.so libm.so
         gtk3 libgtk-3.so
         libevent
         libffi libffi.so
         libpulse libpulse.so
         nss # libnss3.so
         zlib libz.so)
makedepends=(clang
             git
             gn
             gperf
             # harfbuzz-icu # disabled because ICU 76 not supported yet
             java-runtime-headless
             libnotify
             libva
             lld
             llvm
             ninja
             # Electron ships a vendored nodejs. Meanwhile the npm dependency pulls in nodejs which is Arch's freshest version.
             # Pinning the closest LTS here makes the build environment more consistent with the vendored copy.
             nodejs-lts-iron
             npm
             patchutils
             pciutils
             pipewire
             python
             python-requests
             qt5-base
             rsync
             rust
             rust-bindgen
             wget
             yarn)
optdepends=('kde-cli-tools: file deletion support (kioclient5)'
            'pipewire: WebRTC desktop sharing under Wayland'
            'qt5-base: enable Qt5 with --enable-features=AllowQt'
            'gtk4: for --gtk-version=4 (GTK4 IME might work better on Wayland)'
            'trash-cli: file deletion support (trash-put)'
            'xdg-utils: open URLs with desktop’s default (xdg-email, xdg-open)')
options=('!lto') # Electron adds its own flags for ThinLTO
source=("git+https://github.com/electron/electron.git#tag=v$pkgver"
        https://gitlab.com/Matt.Jolly/chromium-patches/-/archive/$_gcc_patches/chromium-patches-$_gcc_patches.tar.bz2
        # Chromium
        chromium-138-nodejs-version-check.patch
        chromium-vesktop.patch
        compiler-rt-adjust-paths.patch
        disable-clang-fextend-variable-liveness.patch
        pdfium-fix-build-with-system-libpng.patch
        # Electron
        default_app-icon.patch
        electron-launcher.sh
        electron.desktop
        jinja-python-3.10.patch
        use-system-libraries-in-node.patch
        makepkg-source-roller.py
        # BEGIN managed sources
        chromium-mirror::git+https://github.com/chromium/chromium.git#tag=138.0.7204.97
        chromium-mirror_third_party_nan::git+https://github.com/nodejs/nan.git#commit=e14bdcd1f72d62bca1d541b66da43130384ec213
        chromium-mirror_third_party_electron_node::git+https://github.com/nodejs/node.git#tag=v22.17.0
        chromium-mirror_third_party_engflow-reclient-configs::git+https://github.com/EngFlow/reclient-configs.git#commit=955335c30a752e9ef7bff375baab5e0819b6c00d
        chromium-mirror_third_party_clang-format_script::git+https://chromium.googlesource.com/external/github.com/llvm/llvm-project/clang/tools/clang-format.git#commit=37f6e68a107df43b7d7e044fd36a13cbae3413f2
        chromium-mirror_third_party_compiler-rt_src::git+https://chromium.googlesource.com/external/github.com/llvm/llvm-project/compiler-rt.git#commit=57196dd146582915c955f6d388e31aea93220c51
        chromium-mirror_third_party_libc++_src::git+https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libcxx.git#commit=a01c02c9d4acbdae3b7e8a2f3ee58579a9c29f96
        chromium-mirror_third_party_libc++abi_src::git+https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libcxxabi.git#commit=9810fb23f6ba666f017c2b67c67de2bcac2b44bd
        chromium-mirror_third_party_libunwind_src::git+https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libunwind.git#commit=8575f4ae4fcf8892938bd9766cf1a5c90a0ed04e
        chromium-mirror_third_party_llvm-libc_src::git+https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libc.git#commit=9c3ae3120fe83b998d0498dcc9ad3a56c29fad0c
        chromium-mirror_media_cdm_api::git+https://chromium.googlesource.com/chromium/cdm.git#commit=852a81f0ae3ab350041d2e44d207a42fb0436ae1
        chromium-mirror_native_client::git+https://chromium.googlesource.com/native_client/src/native_client.git#commit=e3fce84f253bc1e77bb239185c0fbff23dc8e3ee
        chromium-mirror_net_third_party_quiche_src::git+https://quiche.googlesource.com/quiche.git#commit=3b42119c3e4be5d4720c3c1b384106fa43e9b5e3
        chromium-mirror_third_party_angle::git+https://chromium.googlesource.com/angle/angle.git#commit=df15136b959fc60c230265f75ee7fc75c96e8250
        chromium-mirror_third_party_anonymous_tokens_src::git+https://chromium.googlesource.com/external/github.com/google/anonymous-tokens.git#commit=d708a2602a5947ee068f784daa1594a673d47c4a
        chromium-mirror_third_party_content_analysis_sdk_src::git+https://chromium.googlesource.com/external/github.com/chromium/content_analysis_sdk.git#commit=9a408736204513e0e95dd2ab3c08de0d95963efc
        chromium-mirror_third_party_dav1d_libdav1d::git+https://chromium.googlesource.com/external/github.com/videolan/dav1d.git#commit=8d956180934f16244bdb58b39175824775125e55
        chromium-mirror_third_party_dawn::git+https://dawn.googlesource.com/dawn.git#commit=86772f20cca54b46f62b65ece1ef61224aef09db
        chromium-mirror_third_party_highway_src::git+https://chromium.googlesource.com/external/github.com/google/highway.git#commit=00fe003dac355b979f36157f9407c7c46448958e
        chromium-mirror_third_party_boringssl_src::git+https://boringssl.googlesource.com/boringssl.git#commit=9295969e1dad2c31d0d99481734c1c68dcbc6403
        chromium-mirror_third_party_breakpad_breakpad::git+https://chromium.googlesource.com/breakpad/breakpad.git#commit=2625edb085169e92cf036c236ac79ab594a7b1cc
        chromium-mirror_third_party_cast_core_public_src::git+https://chromium.googlesource.com/cast_core/public.git#commit=f5ee589bdaea60418f670fa176be15ccb9a34942
        chromium-mirror_third_party_catapult::git+https://chromium.googlesource.com/catapult.git#commit=5477c6dfde1132b685c73edc16e1bc71449a691d
        chromium-mirror_third_party_ced_src::git+https://chromium.googlesource.com/external/github.com/google/compact_enc_det.git#commit=ba412eaaacd3186085babcd901679a48863c7dd5
        chromium-mirror_third_party_cld_3_src::git+https://chromium.googlesource.com/external/github.com/google/cld_3.git#commit=b48dc46512566f5a2d41118c8c1116c4f96dc661
        chromium-mirror_third_party_colorama_src::git+https://chromium.googlesource.com/external/colorama.git#commit=3de9f013df4b470069d03d250224062e8cf15c49
        chromium-mirror_third_party_cpu_features_src::git+https://chromium.googlesource.com/external/github.com/google/cpu_features.git#commit=936b9ab5515dead115606559502e3864958f7f6e
        chromium-mirror_third_party_cpuinfo_src::git+https://chromium.googlesource.com/external/github.com/pytorch/cpuinfo.git#commit=39ea79a3c132f4e678695c579ea9353d2bd29968
        chromium-mirror_third_party_crc32c_src::git+https://chromium.googlesource.com/external/github.com/google/crc32c.git#commit=d3d60ac6e0f16780bcfcc825385e1d338801a558
        chromium-mirror_third_party_cros_system_api::git+https://chromium.googlesource.com/chromiumos/platform2/system_api.git#commit=fe88d943e5f328b34e38b91296db39650f6ec6f3
        chromium-mirror_third_party_depot_tools::git+https://chromium.googlesource.com/chromium/tools/depot_tools.git#commit=a8900cc0f023d6a662eb66b317e8ddceeb113490
        chromium-mirror_third_party_devtools-frontend_src::git+https://chromium.googlesource.com/devtools/devtools-frontend.git#commit=f8dfe8b36e516cef8a5a169e88d16480d8abdc68
        chromium-mirror_third_party_dom_distiller_js_dist::git+https://chromium.googlesource.com/chromium/dom-distiller/dist.git#commit=199de96b345ada7c6e7e6ba3d2fa7a6911b8767d
        chromium-mirror_third_party_dragonbox_src::git+https://chromium.googlesource.com/external/github.com/jk-jeon/dragonbox.git#commit=6c7c925b571d54486b9ffae8d9d18a822801cbda
        chromium-mirror_third_party_eigen3_src::git+https://chromium.googlesource.com/external/gitlab.com/libeigen/eigen.git#commit=ae3aba99db4c829b4cc4d9fdd54321dedd814dc4
        chromium-mirror_third_party_farmhash_src::git+https://chromium.googlesource.com/external/github.com/google/farmhash.git#commit=816a4ae622e964763ca0862d9dbd19324a1eaf45
        chromium-mirror_third_party_fast_float_src::git+https://chromium.googlesource.com/external/github.com/fastfloat/fast_float.git#commit=cb1d42aaa1e14b09e1452cfdef373d051b8c02a4
        chromium-mirror_third_party_ffmpeg::git+https://chromium.googlesource.com/chromium/third_party/ffmpeg.git#commit=dcdd0fa51b65a0b1688ff6b8f0cc81908f09ded2
        chromium-mirror_third_party_flac::git+https://chromium.googlesource.com/chromium/deps/flac.git#commit=689da3a7ed50af7448c3f1961d1791c7c1d9c85c
        chromium-mirror_third_party_flatbuffers_src::git+https://chromium.googlesource.com/external/github.com/google/flatbuffers.git#commit=8db59321d9f02cdffa30126654059c7d02f70c32
        chromium-mirror_third_party_fontconfig_src::git+https://chromium.googlesource.com/external/fontconfig.git#commit=8cf0ce700a8abe0d97ace4bf7efc7f9534b729ba
        chromium-mirror_third_party_fp16_src::git+https://chromium.googlesource.com/external/github.com/Maratyszcza/FP16.git#commit=0a92994d729ff76a58f692d3028ca1b64b145d91
        chromium-mirror_third_party_gemmlowp_src::git+https://chromium.googlesource.com/external/github.com/google/gemmlowp.git#commit=13d57703abca3005d97b19df1f2db731607a7dc2
        chromium-mirror_third_party_freetype_src::git+https://chromium.googlesource.com/chromium/src/third_party/freetype2.git#commit=738905b34bd1f5a8ff51bd2bc8e38a2d8be9bfd6
        chromium-mirror_third_party_fxdiv_src::git+https://chromium.googlesource.com/external/github.com/Maratyszcza/FXdiv.git#commit=63058eff77e11aa15bf531df5dd34395ec3017c8
        chromium-mirror_third_party_harfbuzz-ng_src::git+https://chromium.googlesource.com/external/github.com/harfbuzz/harfbuzz.git#commit=9f83bbbe64654b45ba5bb06927ff36c2e7588495
        chromium-mirror_third_party_ink_src::git+https://chromium.googlesource.com/external/github.com/google/ink.git#commit=da9cb551ada1e55309b0ac89b9fbff2d29dbfe1e
        chromium-mirror_third_party_ink_stroke_modeler_src::git+https://chromium.googlesource.com/external/github.com/google/ink-stroke-modeler.git#commit=03db1ed37b8b10b47d62ed0fa142d198a3861689
        chromium-mirror_third_party_instrumented_libs::git+https://chromium.googlesource.com/chromium/third_party/instrumented_libraries.git#commit=69015643b3f68dbd438c010439c59adc52cac808
        chromium-mirror_third_party_emoji-segmenter_src::git+https://chromium.googlesource.com/external/github.com/google/emoji-segmenter.git#commit=955936be8b391e00835257059607d7c5b72ce744
        chromium-mirror_third_party_ots_src::git+https://chromium.googlesource.com/external/github.com/khaledhosny/ots.git#commit=46bea9879127d0ff1c6601b078e2ce98e83fcd33
        chromium-mirror_third_party_libgav1_src::git+https://chromium.googlesource.com/codecs/libgav1.git#commit=c05bf9be660cf170d7c26bd06bb42b3322180e58
        chromium-mirror_third_party_googletest_src::git+https://chromium.googlesource.com/external/github.com/google/googletest.git#commit=09ffd0015395354774c059a17d9f5bee36177ff9
        chromium-mirror_third_party_hunspell_dictionaries::git+https://chromium.googlesource.com/chromium/deps/hunspell_dictionaries.git#commit=41cdffd71c9948f63c7ad36e1fb0ff519aa7a37e
        chromium-mirror_third_party_icu::git+https://chromium.googlesource.com/chromium/deps/icu.git#commit=b929596baebf0ab4ac7ec07f38365db4c50a559d
        chromium-mirror_third_party_jsoncpp_source::git+https://chromium.googlesource.com/external/github.com/open-source-parsers/jsoncpp.git#commit=42e892d96e47b1f6e29844cc705e148ec4856448
        chromium-mirror_third_party_leveldatabase_src::git+https://chromium.googlesource.com/external/leveldb.git#commit=4ee78d7ea98330f7d7599c42576ca99e3c6ff9c5
        chromium-mirror_third_party_domato_src::git+https://chromium.googlesource.com/external/github.com/googleprojectzero/domato.git#commit=053714bccbda79cf76dac3fee48ab2b27f21925e
        chromium-mirror_third_party_libaddressinput_src::git+https://chromium.googlesource.com/external/libaddressinput.git#commit=2610f7b1043d6784ada41392fc9392d1ea09ea07
        chromium-mirror_third_party_libaom_source_libaom::git+https://aomedia.googlesource.com/aom.git#commit=2cca4aba034f99842c2e6cdc173f83801d289764
        chromium-mirror_third_party_crabbyavif_src::git+https://chromium.googlesource.com/external/github.com/webmproject/CrabbyAvif.git#commit=eb883022a5886739f07f0241f918e2be97d65ff0
        chromium-mirror_third_party_nearby_src::git+https://chromium.googlesource.com/external/github.com/google/nearby-connections.git#commit=959322177f40f2e0f1ecacd8a1aea2805e67b62b
        chromium-mirror_third_party_securemessage_src::git+https://chromium.googlesource.com/external/github.com/google/securemessage.git#commit=fa07beb12babc3b25e0c5b1f38c16aa8cb6b8f84
        chromium-mirror_third_party_jetstream_main::git+https://chromium.googlesource.com/external/github.com/WebKit/JetStream.git#commit=539ab943598b505832a25a2222aa8957f1a20d6f
        chromium-mirror_third_party_ukey2_src::git+https://chromium.googlesource.com/external/github.com/google/ukey2.git#commit=0275885d8e6038c39b8a8ca55e75d1d4d1727f47
        chromium-mirror_third_party_cros-components_src::git+https://chromium.googlesource.com/external/google3/cros_components.git#commit=97dc8c7a1df880206cc54d9913a7e9d73677072a
        chromium-mirror_third_party_libdrm_src::git+https://chromium.googlesource.com/chromiumos/third_party/libdrm.git#commit=ad78bb591d02162d3b90890aa4d0a238b2a37cde
        chromium-mirror_third_party_expat_src::git+https://chromium.googlesource.com/external/github.com/libexpat/libexpat.git#commit=69d6c054c1bd5258c2a13405a7f5628c72c177c2
        chromium-mirror_third_party_libipp_libipp::git+https://chromium.googlesource.com/chromiumos/platform2/libipp.git#commit=2209bb84a8e122dab7c02fe66cc61a7b42873d7f
        chromium-mirror_third_party_libjpeg_turbo::git+https://chromium.googlesource.com/chromium/deps/libjpeg_turbo.git#commit=e14cbfaa85529d47f9f55b0f104a579c1061f9ad
        chromium-mirror_third_party_liblouis_src::git+https://chromium.googlesource.com/external/liblouis-github.git#commit=9700847afb92cb35969bdfcbbfbbb74b9c7b3376
        chromium-mirror_third_party_libphonenumber_dist::git+https://chromium.googlesource.com/external/libphonenumber.git#commit=9d46308f313f2bf8dbce1dfd4f364633ca869ca7
        chromium-mirror_third_party_libprotobuf-mutator_src::git+https://chromium.googlesource.com/external/github.com/google/libprotobuf-mutator.git#commit=7bf98f78a30b067e22420ff699348f084f802e12
        chromium-mirror_third_party_libsrtp::git+https://chromium.googlesource.com/chromium/deps/libsrtp.git#commit=a52756acb1c5e133089c798736dd171567df11f5
        chromium-mirror_third_party_libsync_src::git+https://chromium.googlesource.com/aosp/platform/system/core/libsync.git#commit=f4f4387b6bf2387efbcfd1453af4892e8982faf6
        chromium-mirror_third_party_libva-fake-driver_src::git+https://chromium.googlesource.com/chromiumos/platform/libva-fake-driver.git#commit=a9bcab9cd6b15d4e3634ca44d5e5f7652c612194
        chromium-mirror_third_party_libvpx_source_libvpx::git+https://chromium.googlesource.com/webm/libvpx.git#commit=b84ca9b63730e7d4563573a56a66317eb0087ebf
        chromium-mirror_third_party_libwebm_source::git+https://chromium.googlesource.com/webm/libwebm.git#commit=c4522d6cd68582d66f1adfd24debfa9bee202afa
        chromium-mirror_third_party_libwebp_src::git+https://chromium.googlesource.com/webm/libwebp.git#commit=2af6c034ac871c967e04c8c9f8bf2dbc2e271b18
        chromium-mirror_third_party_libyuv::git+https://chromium.googlesource.com/libyuv/libyuv.git#commit=61bdaee13a701d2b52c6dc943ccc5c888077a591
        chromium-mirror_third_party_lss::git+https://chromium.googlesource.com/linux-syscall-support.git#commit=ed31caa60f20a4f6569883b2d752ef7522de51e0
        chromium-mirror_third_party_material_color_utilities_src::git+https://chromium.googlesource.com/external/github.com/material-foundation/material-color-utilities.git#commit=13434b50dcb64a482cc91191f8cf6151d90f5465
        chromium-mirror_third_party_minigbm_src::git+https://chromium.googlesource.com/chromiumos/platform/minigbm.git#commit=3018207f4d89395cc271278fb9a6558b660885f5
        chromium-mirror_third_party_nasm::git+https://chromium.googlesource.com/chromium/deps/nasm.git#commit=9f916e90e6fc34ec302573f6ce147e43e33d68ca
        chromium-mirror_third_party_neon_2_sse_src::git+https://chromium.googlesource.com/external/github.com/intel/ARM_NEON_2_x86_SSE.git#commit=eb8b80b28f956275e291ea04a7beb5ed8289e872
        chromium-mirror_third_party_openh264_src::git+https://chromium.googlesource.com/external/github.com/cisco/openh264.git#commit=652bdb7719f30b52b08e506645a7322ff1b2cc6f
        chromium-mirror_third_party_openscreen_src::git+https://chromium.googlesource.com/openscreen.git#commit=8cc5a0e8f6695263d44206cf5930641979cb3179
        chromium-mirror_third_party_openxr_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/OpenXR-SDK.git#commit=781f2eab3698d653c804ecbd11e0aed47eaad1c6
        chromium-mirror_third_party_pdfium::git+https://pdfium.googlesource.com/pdfium.git#commit=cf433ae5520d061db56391155b59b34e67484f39
        chromium-mirror_third_party_perfetto_3b5d0997::git+https://chromium.googlesource.com/external/github.com/google/perfetto.git#commit=dd35b295cd359ba094404218414955f961a0d6ae
        chromium-mirror_third_party_protobuf-javascript_src::git+https://chromium.googlesource.com/external/github.com/protocolbuffers/protobuf-javascript.git#commit=28bf5df73ef2f345a936d9cc95d64ba8ed426a53
        chromium-mirror_third_party_pthreadpool_src_934f177b::git+https://chromium.googlesource.com/external/github.com/google/pthreadpool.git#commit=dcc9f28589066af0dbd4555579281230abbf74dd
        chromium-mirror_third_party_pyelftools::git+https://chromium.googlesource.com/chromiumos/third_party/pyelftools.git#commit=19b3e610c86fcadb837d252c794cb5e8008826ae
        chromium-mirror_third_party_quic_trace_src::git+https://chromium.googlesource.com/external/github.com/google/quic-trace.git#commit=ed3deb8a056b260c59f2fd42af6dfa3db48a8cad
        chromium-mirror_third_party_pywebsocket3_src::git+https://chromium.googlesource.com/external/github.com/GoogleChromeLabs/pywebsocket3.git#commit=50602a14f1b6da17e0b619833a13addc6ea78bc2
        chromium-mirror_third_party_re2_src::git+https://chromium.googlesource.com/external/github.com/google/re2.git#commit=c84a140c93352cdabbfb547c531be34515b12228
        chromium-mirror_third_party_ruy_src::git+https://chromium.googlesource.com/external/github.com/google/ruy.git#commit=83fd40d730feb0804fafbc2d8814bcc19a17b2e5
        chromium-mirror_third_party_search_engines_data_resources::git+https://chromium.googlesource.com/external/search_engines_data.git#commit=09fd22f3a4fb77ab03b7734e0c03ff7d7f97ef88
        chromium-mirror_third_party_skia::git+https://skia.googlesource.com/skia.git#commit=a46d5732d9fca93eaec23e502e2eef814b707e6b
        chromium-mirror_third_party_smhasher_src::git+https://chromium.googlesource.com/external/smhasher.git#commit=0ff96f7835817a27d0487325b6c16033e2992eb5
        chromium-mirror_third_party_snappy_src::git+https://chromium.googlesource.com/external/github.com/google/snappy.git#commit=32ded457c0b1fe78ceb8397632c416568d6714a0
        chromium-mirror_third_party_sqlite_src::git+https://chromium.googlesource.com/chromium/deps/sqlite.git#commit=0a1397d274701c5d39e661e948160da2b9a8db1e
        chromium-mirror_third_party_swiftshader::git+https://swiftshader.googlesource.com/SwiftShader.git#commit=a8133cbb3c8969e3c1e6b3cea2c02ec8312ef9ca
        chromium-mirror_third_party_text-fragments-polyfill_src::git+https://chromium.googlesource.com/external/github.com/GoogleChromeLabs/text-fragments-polyfill.git#commit=c036420683f672d685e27415de0a5f5e85bdc23f
        chromium-mirror_third_party_tflite_src::git+https://chromium.googlesource.com/external/github.com/tensorflow/tensorflow.git#commit=151774faba661a5985a8264653f4457c70a56dea
        chromium-mirror_third_party_vulkan-deps::git+https://chromium.googlesource.com/vulkan-deps.git#commit=5912cbdd295c2bacb5798432a7b1cac9d20c0725
        chromium-mirror_third_party_glslang_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/glslang.git#commit=93231001597dad1149a5d035af30eda50b9e6b6c
        chromium-mirror_third_party_spirv-cross_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/SPIRV-Cross.git#commit=b8fcf307f1f347089e3c46eb4451d27f32ebc8d3
        chromium-mirror_third_party_spirv-headers_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/SPIRV-Headers.git#commit=c9aad99f9276817f18f72a4696239237c83cb775
        chromium-mirror_third_party_spirv-tools_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/SPIRV-Tools.git#commit=01021466b5e71deaac9054f56082566c782bfd51
        chromium-mirror_third_party_vulkan-headers_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/Vulkan-Headers.git#commit=75ad707a587e1469fb53a901b9b68fe9f6fbc11f
        chromium-mirror_third_party_vulkan-loader_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/Vulkan-Loader.git#commit=c913466fdc5004584890f89ff91121bdb2ffd4ba
        chromium-mirror_third_party_vulkan-tools_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/Vulkan-Tools.git#commit=60b640cb931814fcc6dabe4fc61f4738c56579f6
        chromium-mirror_third_party_vulkan-utility-libraries_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/Vulkan-Utility-Libraries.git#commit=49ac28931f28bffaa3cd73dc4ad997284d574962
        chromium-mirror_third_party_vulkan-validation-layers_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/Vulkan-ValidationLayers.git#commit=f7ceb1d01a292846db77ec87786be84d6fd568d9
        chromium-mirror_third_party_vulkan_memory_allocator::git+https://chromium.googlesource.com/external/github.com/GPUOpen-LibrariesAndSDKs/VulkanMemoryAllocator.git#commit=56300b29fbfcc693ee6609ddad3fdd5b7a449a21
        chromium-mirror_third_party_wayland_src::git+https://chromium.googlesource.com/external/anongit.freedesktop.org/git/wayland/wayland.git#commit=a156431ea66fe67d69c9fbba8a8ad34dabbab81c
        chromium-mirror_third_party_wayland-protocols_src::git+https://chromium.googlesource.com/external/anongit.freedesktop.org/git/wayland/wayland-protocols.git#commit=7d5a3a8b494ae44cd9651f9505e88a250082765e
        chromium-mirror_third_party_wayland-protocols_kde::git+https://chromium.googlesource.com/external/github.com/KDE/plasma-wayland-protocols.git#commit=0b07950714b3a36c9b9f71fc025fc7783e82926e
        chromium-mirror_third_party_wayland-protocols_gtk::git+https://chromium.googlesource.com/external/github.com/GNOME/gtk.git#commit=40ebed3a03aef096addc0af09fec4ec529d882a0
        chromium-mirror_third_party_webdriver_pylib::git+https://chromium.googlesource.com/external/github.com/SeleniumHQ/selenium/py.git#commit=fc5e7e70c098bfb189a9a74746809ad3c5c34e04
        chromium-mirror_third_party_webgl_src::git+https://chromium.googlesource.com/external/khronosgroup/webgl.git#commit=c01b768bce4a143e152c1870b6ba99ea6267d2b0
        chromium-mirror_third_party_webpagereplay::git+https://chromium.googlesource.com/webpagereplay.git#commit=18172a359f6dab8e3f70b6c5c8c7c55d3e97537a
        chromium-mirror_third_party_webrtc::git+https://webrtc.googlesource.com/src.git#commit=e4445e46a910eb407571ec0b0b8b7043562678cf
        chromium-mirror_third_party_wuffs_src::git+https://skia.googlesource.com/external/github.com/google/wuffs-mirror-release-c.git#commit=e3f919ccfe3ef542cfc983a82146070258fb57f8
        chromium-mirror_third_party_weston_src::git+https://chromium.googlesource.com/external/anongit.freedesktop.org/git/wayland/weston.git#commit=4eb10b123b483327214d8da5da67e8bbeeaed8fe
        chromium-mirror_third_party_xdg-utils::git+https://chromium.googlesource.com/chromium/deps/xdg-utils.git#commit=cb54d9db2e535ee4ef13cc91b65a1e2741a94a44
        chromium-mirror_third_party_xnnpack_src::git+https://chromium.googlesource.com/external/github.com/google/XNNPACK.git#commit=f82ad65ca52cb4d39b73088468a5fe00f56fb47c
        chromium-mirror_third_party_zstd_src::git+https://chromium.googlesource.com/external/github.com/facebook/zstd.git#commit=f9938c217da17ec3e9dcd2a2d99c5cf39536aeb9
        chromium-mirror_v8::git+https://chromium.googlesource.com/v8/v8.git#commit=e5b4c78b54e8b033b2701db3df0bf67d3030e4c1
        chromium-mirror_third_party_angle_third_party_glmark2_src::git+https://chromium.googlesource.com/external/github.com/glmark2/glmark2.git#commit=6edcf02205fd1e8979dc3f3964257a81959b80c8
        chromium-mirror_third_party_angle_third_party_rapidjson_src::git+https://chromium.googlesource.com/external/github.com/Tencent/rapidjson.git#commit=781a4e667d84aeedbeb8184b7b62425ea66ec59f
        chromium-mirror_third_party_angle_third_party_VK-GL-CTS_src::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/VK-GL-CTS.git#commit=c9d2e24d1a6da00165a0b5908ea4ba05c2e5f0b2
        chromium-mirror_third_party_dawn_buildtools::git+https://chromium.googlesource.com/chromium/src/buildtools.git#commit=244e7cf4453305d0c17d500662a69fba2e46a73e
        chromium-mirror_third_party_dawn_build::git+https://chromium.googlesource.com/chromium/src/build.git#commit=db0d31d702840881c049c523a2226e8e391929bf
        chromium-mirror_third_party_dawn_tools_clang::git+https://chromium.googlesource.com/chromium/src/tools/clang.git#commit=5d9b09742311e059ecdba6d74adcb883e4ebffe5
        chromium-mirror_third_party_dawn_tools_mb::git+https://chromium.googlesource.com/chromium/src/tools/mb.git#commit=61f390a8b5da670b755e021a9ec0c2cac3de840e
        chromium-mirror_third_party_dawn_third_party_jinja2::git+https://chromium.googlesource.com/chromium/src/third_party/jinja2.git#commit=e2d024354e11cc6b041b0cff032d73f0c7e43a07
        chromium-mirror_third_party_dawn_third_party_markupsafe::git+https://chromium.googlesource.com/chromium/src/third_party/markupsafe.git#commit=0bad08bb207bbfc1d6f3bbc82b9242b0c50e5794
        chromium-mirror_third_party_dawn_third_party_glfw::git+https://chromium.googlesource.com/external/github.com/glfw/glfw.git#commit=b35641f4a3c62aa86a0b3c983d163bc0fe36026d
        chromium-mirror_third_party_dawn_third_party_zlib::git+https://chromium.googlesource.com/chromium/src/third_party/zlib.git#commit=209717dd69cd62f24cbacc4758261ae2dd78cfac
        chromium-mirror_third_party_dawn_third_party_abseil-cpp::git+https://chromium.googlesource.com/chromium/src/third_party/abseil-cpp.git#commit=04dc59d2c83238cb1fcb49083e5e416643a899ce
        chromium-mirror_third_party_dawn_third_party_dxc::git+https://chromium.googlesource.com/external/github.com/microsoft/DirectXShaderCompiler.git#commit=d72e2b1a15d22fc825e2f3c939f1baac43281ae9
        chromium-mirror_third_party_dawn_third_party_dxheaders::git+https://chromium.googlesource.com/external/github.com/microsoft/DirectX-Headers.git#commit=980971e835876dc0cde415e8f9bc646e64667bf7
        chromium-mirror_third_party_dawn_third_party_khronos_OpenGL-Registry::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/OpenGL-Registry.git#commit=5bae8738b23d06968e7c3a41308568120943ae77
        chromium-mirror_third_party_dawn_third_party_khronos_EGL-Registry::git+https://chromium.googlesource.com/external/github.com/KhronosGroup/EGL-Registry.git#commit=7dea2ed79187cd13f76183c4b9100159b9e3e071
        chromium-mirror_third_party_dawn_third_party_webgpu-headers_src::git+https://chromium.googlesource.com/external/github.com/webgpu-native/webgpu-headers.git#commit=60cd9020309b87a30cd7240aad32accd24262a5e
        chromium-mirror_third_party_dawn_third_party_protobuf::git+https://chromium.googlesource.com/chromium/src/third_party/protobuf.git#commit=1a4051088b71355d44591172c474304331aaddad
        chromium-mirror_third_party_dawn_tools_protoc_wrapper::git+https://chromium.googlesource.com/chromium/src/tools/protoc_wrapper.git#commit=8ad6d21544b14c7f753852328d71861b363cc512
        chromium-mirror_third_party_dawn_third_party_partition_alloc::git+https://chromium.googlesource.com/chromium/src/base/allocator/partition_allocator.git#commit=2041003ba674f918c33b1afaaad74e652f34bcea
        chromium-mirror_third_party_openscreen_src_third_party_tinycbor_src::git+https://chromium.googlesource.com/external/github.com/intel/tinycbor.git#commit=d393c16f3eb30d0c47e6f9d92db62272f0ec4dc7
        # END managed sources
        )
sha256sums=('7e01be024b2a068b41028776d14eef98e4c9ccb0aef78fd226677c9c0c0023ee'
            '6f5067e5f87ac0591295fc3ec0f7e722d0f5eb94ade2fb3e73ae8abcbb674f8a'
            '11a96ffa21448ec4c63dd5c8d6795a1998d8e5cd5a689d91aea4d2bdd13fb06e'
            '86b2896bf4d2c770eb1aefaf276a1eabbb0858c94722cae476d2d01efbc2cd15'
            '750fa28c0cbe464a45bab5a1021434e296ad83fef78b927eaec0f82df3aac26c'
            '2d98a7a6a553fb5c17c4bfe36f011410f377afa12a6a818ba36543dc9a258f4a'
            'de3222b13d3a49628a00fd74acae633912b830f78c2de452d3bdff3d0e42026d'
            'dd2d248831dd4944d385ebf008426e66efe61d6fdf66f8932c963a12167947b4'
            '13fcf26193f4417fd5dfbc82a3f24e5c7a1cce82f729f6a73f1b1d3a7b580b34'
            '4484200d90b76830b69eea3a471c103999a3ce86bb2c29e6c14c945bf4102bae'
            '55dbe71dbc1f3ab60bf1fa79f7aea7ef1fe76436b1d7df48728a1f8227d2134e'
            '991e54f4490cdbb5e52c9a4a4f6e0e32f2fc95979f18a4736016d065da229c2e'
            '9425aae442643db1760a4d4b41bda9f3dfb8691fdc9e9ba17531d03cb13d0bc5'
            'c589d5a274f44dc62c5f14e392723b38072c9d52035f323a6329b8c182986c93'
            '0b7a546ee6913c49519c10c293ac530ff381641a8a465fa2e184d6dbe0fb784d'
            '12df8c956282bdbf0a3af78f8b0b476b943d630315a0710e88435a692e3624ee'
            '3522166c3ca75316a172b7cc4fe12bba9367e30fed16df8193ede2e236dca8c5'
            '60935b226794933e881973746d892eb6fb7b7d596bf6cf9ff3c4f2da56240a9b'
            'd5bc28d4287277508f12d664a2942c349cdb38985907f85065adfb8dff41f653'
            'e90f765b9b7561e33aeb1fab3a53f22a28c40bd71df854da9330e3e7061c38f9'
            'ba2f65c0efca9465b8757e3272287d9a58bb8bb03a89cf2eb09ef8ae73296fab'
            'e5087a6faa6979a4880a7c1353338fcad1b80ce154fa335f4d47213eee83b354'
            'b34498c54f5c02b368093265ccf893b32693fb92f3911d7155cedecac2f1af7a'
            'acd65ef94e07408dc84165fc32c4154adbdb9a9d1f1e904e44b6b5dfad776743'
            '955b59a69f23ed5ad0db5d97a11a85370729e8b570e769e709d5bdd0f2268194'
            '78d5c79f5f7f3dde9b7a3f6baf402a30f341c10877b69ef4e735d120b0c3792a'
            'dfc90aefd191d9dfcf3c464325497aef2e891ef1577252cf515f99d4e88d226e'
            'ee540040f1518dad802758f97cce3944ac9491f58ff3be5af66497dfed8cafb0'
            '89a368f0652d857d38402d6f3c5cded3c1757230ab7abe01df850a7bf8359119'
            '9336770d8ccf16ec07b3037539b25c34ea04d1378b4a40686122f623f9500c3e'
            '3473ac374def115bc2df146bba79f3dea7fc42d338ada97ebc6aebfc8eecec41'
            '5f359dae10e80599f26483879b879d7a6808520d4a56c98ee0879373a6339619'
            '72766eee3e731c50aa775e8d52416aca6a0c3a53ccd9041d2ea046e13772e8e5'
            'b0d84c34304f6ee7174c4762f95bb737faf69bef69812c29ed62df8952de9f39'
            'da13009001bb6b7a47ac1351b017c2c37320b9a3290f222d3d82b583b630d49a'
            '049254cf966a3fab3c696c29d23ccc4e7752ae5e02ec01e1f9f73aff9acba466'
            '8b97c25874c17644300d1cbe6ac1fceb705bf18297e27699ba20497fc47ae239'
            'e6a28c25e3d93c9c37414149ff44ac7a1bbb4d8a167061f8ee9679dc065af1bb'
            '9e950d9f0bf7f0b52de6744de0922583b4b32281e87f0488c2d1cfc533665aa5'
            '6125206b56f365874ba812038dbcd4271f8a73235ab4d211c42b7fd2d636bbc8'
            '75290e49d4726b020318e638d439ff40110e0940a0923e257f03caa473d33f9a'
            '6ae7ae01b3c23f8bf7657a59427aac6f3216e041ebdb983b82c002a949bdb071'
            '4b9855f53a18eefcef43bb64534f4aa82e756384b847c7d4b03073989415ee32'
            '1b014921a3ee7f52b8d8aaa07c1495c9f4002f343cc561fd80bb63a905ec3a88'
            'fcf628ecff962a1ebc9b3daa9fed2fa10352a935b54ecae0095ef8dda3a9588e'
            '47f3f3d044cc0658274833022db1e7695964b1da8f37cb905882d15457212fba'
            '7a6c373f8694e540f5a767b315670ccef5526baa41f5427f02db2e4bf261765c'
            'ee63da5c2b0efd2e2d919070ea1e2da73407020c7563d4ed69d586c101a2443c'
            '6258126c4c354ccacd0ec5f9f82c6970d576359c7aba86e44277b459d1645325'
            'be05ebb53b7468e246aac2a22d1ce748c25e2e0cc5d0227e16272a00827092ff'
            '8708023dc5aec3ebd5e05677b3f44d7676e287bfc755937bcd6356876e8415e6'
            'cf96ae84ef29434dd20b0f2daca6013373dd6e47c87cde3aa03abce0500a9f03'
            '7df2a26df1b8e69c58692295443e18de9f19bc0107bd5911beed53157a592ad3'
            '06657d77d906f5dda37cb9bc741cfa1792c7ddf88d223ab38696d6e59e5e7255'
            '5d0c4f261d36707f926fa9ef9a39349f1cccac8ae6443a8f8571c1625eb90c41'
            '1a1e2859649a95beef8dba22e8c77735652a212bc88a9bb4dfe1458667dcabbc'
            'ede189b94f6849a538d67fcbe1d73321f1d4c25f9ec5c21c5c9c61baf4a3215b'
            '0f27ab5434870f31886d7c958ced4ff335a09a1080637fb50afdf95db19e3442'
            'aeed970f57904ef9f3b2feee5c50699bd6266b094d10ce53d4bc73a3c82df84a'
            '3ab1e4e2c9a994a0a3c6999c2cbaa9132e7b43e0ab9f92af08331b198a4e9054'
            '2821d4164f4542966269767cee72d6287fd2816344d37bfb6ae979a407729df5'
            'c3db1069a0f69cb2b6cacaaa5a43333799e69a07282b53c5f45383e086833258'
            '66004b44318ad7e4329d65b08320136ee8a9f074b7b001107c52377493d28cc0'
            'af81f653b73270d4b8f9d1e92ecf39821498c08f4ca5c69872e39bac90b40083'
            '488513b955f90b0f965be248631fedab0f27714c49632eb58389c2ff18815199'
            'a3b49ac1e7d4dd6aa75ec771039c522b74b2e2962310060bc44d0a33ab5367b7'
            '92fe0e99dea519a56b80321646b7b2b674564f4e8d036cbbf4d98e8588531720'
            '77b0234b90416961ff07108195c21f5149984629bf72c9c20fcc4f1d2b9d0584'
            '9f58ce3d45baf6796965aa79109af62c330f82b97d320bb5d7bbbdea0e579a92'
            '2c21c74e00540f211bb57b33e8644f8ab2ec511b7b905b432acc163d898cca34'
            'c2eb3aee5d91aa9d80d651d5bc26ae729e9a5bdd2f62985ca394cebac5b8174f'
            'bb19e0319273e64c3eda91786d1bb1c6038cc90e1380c56abcb96a62e29d46ee'
            '79bcb01cf137bfdb97d1e646c3cb72f75c36e4c302e947e84b2b11cd9ef080b3'
            '4e10cd7e19ba51c20df7352f890b622609e4bca1800cc7c34bee01d0147b2f5e'
            '778c634058018b48cdb1ae2a873fb4f5dd8d7463ec8ca1d5cb6ba3a89497be23'
            '66b8f66432b1325861b5f411c71ec49fa171d9a0063bf958242ddde6ce09c12f'
            '87a7c7b4f219a52ad112393eb518f54cdb0e78db21a2be45e5d94e36a542ef82'
            '9c888babaaf59afc855d944e8b26ab573d5e80026dc3bc8dc64720b8f5bb27a2'
            'b3eecfe63f7536930d5772b44d72ad4535663e46b958d098723f0097967d31a3'
            'ae2c189d21dcd056116ee1c3d54b5ae3874e5ac0cc2086c137625b618334cbb1'
            '7101212454ccddf53d69525cf105f0fd6795fd9b1fd948f8c96ac73ce512c41d'
            'fe2f23319ca61ecb2fac8e586ad71fe36ba340fd4f5c4d0372d0e119d5c264e0'
            '080009891e90088f91c9a4fae711fa2bf56599719480e17b108047089798e16e'
            '4070e77bf7afd9fb949067f63c3580d1f5badacfe4c2ab187129ba20446efd04'
            'cf14b8dbbde77c5a844eb06b1869c40342ea41bf1bff8b112ab388729a92f3e0'
            'cb8390c0d03bea1724a2f0c822b46331ff2fd5eac5bbe216f5d229c2c859ee75'
            '867f9d88a2146f54979508a670f28f681c729dd144956941066a422714fbd8c7'
            '9341676174943fbc5268e023c3e572171289fc4748401723a6dcaef50f793dcd'
            '7b81837265657fa3404c93b2de8d5735265dfecc52ec9e5a3157ef4a14cfdba1'
            '4906b9d62e1f9223adad011b19e2720f15a22c35eef1d5c06d8db172a4490d7b'
            '215f2670d14433a13c9cf3961854d26df8a1d00988b363b0c9e276a2242f8d18'
            '453e01c28b9e9c438fe8fedc54dc4c6b1800741e75c93c7cbfb5857378584934'
            'd1562dbb4de0e262826d15a808a06d7f92fe10a7f188507c75a5c588d482c7af'
            '25bc4bf11c958537b4e725542fae58fc1ec00800306cdd70f3c5f94e1a5180df'
            'f2aba031573fc4929d2bd9d03e4b18c4385f399fa0b605eca35898567ebdf7b4'
            '9010695b87eef676b62ec429879972c135987dab6eb53b0a4edf1b5a7cb0bb8b'
            'c77e633ac37c29566eec6f8af3873c7200c550258a90ee26438057e1edf6bcac'
            '34f643fd7cf56634ef1fe040568ebc42329cb8645c98933087a98136468ab671'
            'af96173677a5d2e66a60c0aca3d53e108ead7d4d2007b4ef38b7173131d91447'
            '6e5548c7a28d49d485147076fddf83cb1c84435299fce6b0878d82132d502c2b'
            '602a646863f7c4004376990d9a9339e6ae821d7ea98fe5f675e14eb508fb7747'
            '5208cbe3629515a7b35b13f4f507e4b1e7d79b83737c104b449e7cc6f75bbb85'
            'd67cf07f4ad2aecac9e7665db8e8312da0ceac24b7d9ee2e1668a808cfcedc8d'
            '4eebcfc0488456441b8790d08153c9759c2649acbd23d2293d78cf6dd88f76fb'
            '18ba9daa98e4ff30554fe7b4aaa17a7e5272ac0e7ae2886ffb7f48ae8cdee9d6'
            '99995f0ca85ab0e85bd291e5336657df41409a48ca5439dcaf162d8b11ac0ec6'
            'b641f9f95d9c7b231fc291ee5c1ef5e1badc727200f6dece4a32b92ca730b3df'
            '599bbbabf9e2dc2006dd9e3e9636c4f648360726173793bf6a5a5414698762c5'
            '1130656c814fec74863fb43f9ce698c833f80f4f853870b389af93006ab3d308'
            'e233bbe7474752668e3f1f72f677f532b54526f8891a6160bb87891cba236015'
            'cde69b3ed30cbc32055f507998589b4de1caaf8c5dd26e66bd4687edc5b37ca6'
            'a090c16613c0b1f0e8f8a485e1ec70e4609376b00aa03f10b70f3641b1d92478'
            '4ebe3ffd4fcd7b1057ce72b0439638c43aa8825040be30b11b8b5a5101a06bb0'
            'b07116bf69c635b29f36e097c97445200042b713d5ac8b64a4b95777aa6fc7ee'
            '5c5f90f26c7bbeb29b54832cade629023e55f9a1489fcab4b37a8a5b6d779769'
            '3ccad55267ca0e5f7f07a578f01b659d3346f46e9993babaeb295c9bbf7bb2a4'
            '108a67f21c2bdf2dbc4838f3ba32c992325a29cb62a14b377f8a04a9ad5b2b82'
            '5152142cb9dd205b10223c70574edeec2b3e6e97227c08c2bab4e931ef4c358b'
            '5b6cba7463cc24e69d696db8b11df6f7581db625cd9c32768d04e880ce825c3b'
            'dceb791c3012b48866f297ac9a458b1aa0492b29134a3448dc659fca651efce0'
            '0f18fde832017387600b5ee2ec6a0ae82125c82b97c0f717772f3cd5dfdcd57b'
            'ac2ba9a97065d9fe16288ffb5a8cfa15224a26132f765ed4650255ee2449f8c1'
            '792b4a6b492ffec045b129b166bfc5dec96d4b5564882c312b90bb21b44f667a'
            'a02d697aa28c58646a042ef4ca6f30aa3f3e99a8a326a04891c97b5899d0ff2c'
            'f632b4ead35ef2984f7bd4292dc9a841fbdd1b5925cfc1081bb198cc1496408e'
            '82916d1b7b1ff563617fafdb501d8a42d87559a383b5273700ec70ca62c2cced'
            '8dbffb4595601de3c4ff7b67cca0851c9efe9e24bce29eb1a2358fa9c12be22f'
            'c12fc6b5716a565f196981ffe0be2bf802739d4796c3d9c81ff516d4015438f5'
            '913fc3a85ae676025bafe63880c6413ffafe42495a04a52527ee914ee9ba3ae5'
            '8ee0bade4127e082dc1ae86f0068aa32ea0fbce26069ed2d9dbdef324e1bb980'
            '900f9249e65a3bf0189f3e32c6a2d84bd88b9b3a7d7cfba8c12c1be0d78dd31f'
            '1da28304d237ba934e76394107e46fed0e4120fd2b257f1c667c2d11b52d959b'
            'a9a8839d08232091a0cd381f51380a0a6ebe841f5a8e50a6047aae7b8e34c681'
            '02696a90c7831e3fa903df105573c5f10f4934602fb0e90c846fb44213c40b27'
            '91ef8477f7d670d88f4d8bdeca47aa3b661f6a359fe8ac973bcdf2315affdcda'
            'd73161cc1b733ab88be1d2a0ca0b9b15ef3cc4f636e885af30b22d6c896276a6'
            '461b275d6177f04153dd6522f836a997527d7c4b10d41e823a37be54f2fe8e2f'
            '0c9106a2bef658f02b2312d081faad6ba8a72bbb5b4ee1cae7d0a95e4ef53f8f'
            '552434c4aa5bb9919244051bda20f4641e5be5a9d7d7ec99358da30cfdd49f3e'
            '910bc5d9e7523ccd09506bafe3fac586db5106d8cc72d77e8457fdf8b43c225e'
            'e7ebc82ce1209fb3dd28c25f049f58fe99689b8c3b9a6738a8f1071a53272480'
            '5d472d5395430fb75d7e47c3c87348694473e5956254ea7a9c01e724fd52aec6'
            '3e8a0c5a69c297af03b8502323e0fb3234ab9f650bfe97ea2b6526d0cff9e198'
            '4dfc3a5c54acbdafd4c7ab2826756ac2e69521350ab7f8b80b7ad374ce7ac84f'
            '716cc81139f11a2b438802d37f245f885fc9a0c69ef429a11b156145c903a932'
            '8d0c004e510226c1689c9b902b6ae88c3a0531af71e3b0077734e4c3f33659e6'
            '2c16b2c1e0a92f19a73dd58870f3a6dfa5fbf2e4ed489c08291741a1cda632d9'
            'ab820b7ebb05202369effbf63ee6003daa53a898efc4b60d5c7abbb0a9104fa7'
            'd9d21daad631a71c15abada19bc6edf99bd92b95be663ee19dd1552ea387148e'
            'd127fe8b0dbcef87f258e0228b1d268e505c756982ba08f35db1c214ef6f5dd9'
            'b48490fbcdad8becc160f2dab2ee4a0f67327f1e9d9ddbd96e44150175c68ca9'
            '0b95ed21612b4f02e65643f2029d8ce5710f49dbe8b229350bbe643167a4b83b'
            '9bd1e05f5128b4715c2d354a6895839d01aae4fc9f56b9d0411afc87fb46daf4'
            '3ae63a893b5b585823f04b5a2e604d3df4c7c6e311f5da5b5d5af92a1fd00465'
            'f4de1c27004d328a4434e5ee6b2190e6d7569817ba53673586cd0ffc72e923c7'
            'f68d50065ac94b36910852fce0e262998a492bd531418d7f5b4f9307adfade62'
            'f7f5d15365443cbd8137445c3aedf8ccd31c3402f72c0fa7c16e7bf1c7977139'
            'f8627f5f3a7c119807afc9dc66ce7cb350f905fd1db7fb6b0077552974a07515'
            'ac3f025aa27fec77b24b443df3a69750dc9bb070a40af5180d031b81e66e328c'
            'd4c4ed639439922b3827c72adf8ab870fe54e8b0b86deecd14f61c8143c24a15'
            '0a7ed0c582fe5052af854675b065a5f1b3440b66906343359abee5214c316e2f'
            'c78207d508b9c3314395d294324285fb4a2d8c4e3250818b0558b8491f8f56ac'
            'da0cf693fd872a927776670eed4a53f31cfcf9a02e38d01573caead33dfa83b9'
            'c23fa31250811a76be900554b9ac127f861ebde09c07ac67cd6b82dd214e5686')

# Possible replacements are listed in build/linux/unbundle/replace_gn_files.py
# Keys are the names in the above script; values are the dependencies in Arch
# plus any so names that are provided + linked
declare -gA _system_libs=(
  [brotli]=brotli
  # [dav1d]="dav1d libdav1d.so"
  # [ffmpeg]="ffmpeg libavcodec.so libavcodec.so libavformat.so libavutil.so" # YouTube playback stopped working in Chromium 120
  [flac]="flac libFLAC.so"
  [fontconfig]="fontconfig libfontconfig.so"
  [freetype]="freetype2 libfreetype.so"
  [harfbuzz-ng]="harfbuzz libharfbuzz.so libharfbuzz-subset.so"
  # [icu]="icu libicui18n.so libicuuc.so" # disabled because ICU 76 not supported yet
  # [jsoncpp]="jsoncpp libjsoncpp.so"  # needs libstdc++
  # [libaom]=aom
  # [libavif]=libavif # libavif.so libavutil.so # needs -DAVIF_ENABLE_EXPERIMENTAL_GAIN_MAP=ON
  [libdrm]=libdrm # libdrm.so
  [libjpeg]="libjpeg-turbo libjpeg.so"
  [libpng]="libpng libpng16.so"
  # [libvpx]=libvpx
  # [libwebp]="libwebp libwebpdemux.so libwebpmux.so libwebp.so" # //third_party/libavif:libavif_enc needs //third_party/libwebp:libwebp_sharpyuv
  [libxml]="libxml2 libxml2.so"
  [libxslt]="libxslt libxslt.so"
  [opus]="opus libopus.so"
  # [re2]="re2 libre2.so" # needs libstdc++
  # [snappy]=snappy # libsnappy.so # needs libstdc++
  # [woff2]="woff2 libwoff2dec.so" # needs libstdc++
  [zlib]=minizip # libminizip.so
)
_unwanted_bundled_libs=(
  $(printf "%s\n" ${!_system_libs[@]} | sed 's/^libjpeg$/&_turbo/')
)
depends+=(${_system_libs[@]})

_update_sources() {
  python makepkg-source-roller.py update "v$pkgver" "$pkgname"
  updpkgsums
}

prepare() {
  sed -i "s|@ELECTRON@|${pkgname}|" electron-launcher.sh
  sed -i "s|@ELECTRON@|${pkgname}|" electron.desktop
  sed -i "s|@ELECTRON_NAME@|Electron ${_major_ver} Vesktop|" electron.desktop

  cp -r chromium-mirror_third_party_depot_tools depot_tools
  export PATH+=":$PWD/depot_tools" DEPOT_TOOLS_UPDATE=0
  #export VPYTHON_BYPASS='manually managed python not supported by chrome operations'

  echo "Putting together electron sources"
  # Generate gclient gn args file and prepare-electron-source-tree.sh
  python makepkg-source-roller.py generate electron/DEPS $pkgname
  rbash prepare-electron-source-tree.sh "$CARCH"
  mv electron src/electron

  echo "Running hooks..."
  # depot_tools/gclient.py runhooks
  src/build/landmines.py
  src/build/util/lastchange.py -o src/build/util/LASTCHANGE
  src/build/util/lastchange.py -m GPU_LISTS_VERSION \
    --revision-id-only --header src/gpu/config/gpu_lists_version.h
  src/build/util/lastchange.py -m SKIA_COMMIT_HASH \
    -s src/third_party/skia --header src/skia/ext/skia_commit_hash.h
  src/build/util/lastchange.py \
    -s src/third_party/dawn --revision src/gpu/webgpu/DAWN_VERSION
  src/tools/update_pgo_profiles.py --target=linux update \
    --gs-url-base=chromium-optimization-profiles/pgo_profiles

  # https://gitlab.archlinux.org/archlinux/packaging/packages/electron32/-/issues/1
  src/third_party/node/update_npm_deps

  src/electron/script/apply_all_patches.py \
      src/electron/patches/config.json

  # https://github.com/nodejs/node/issues/48444
  export UV_USE_IO_URING=0

  pushd src
  pushd electron
  yarn install --frozen-lockfile
  popd

  echo "Applying local patches..."

  # https://crbug.com/893950
  sed -i -e 's/\<xmlMalloc\>/malloc/' -e 's/\<xmlFree\>/free/' \
         -e '1i #include <cstdlib>' \
    third_party/blink/renderer/core/xml/*.cc \
    third_party/blink/renderer/core/xml/parser/xml_document_parser.cc \
    third_party/libxml/chromium/*.cc


  # Upstream fixes
  # patch -Np1 -i ../disable-clang-fextend-variable-liveness.patch
  # patch -d third_party/pdfium -Np1 < ../pdfium-fix-build-with-system-libpng.patch

  # Fixes from Gentoo
  patch -Np1 -i ../chromium-138-nodejs-version-check.patch

  # Allow libclang_rt.builtins from compiler-rt >= 16 to be used
  patch -Np1 -i ../compiler-rt-adjust-paths.patch

  # Fixes for building with libstdc++ instead of libc++
  patch -Np1 -i ../chromium-patches-*/chromium-138-compiler.patch

  # Patch chromium PRODUCT_STRING to vesktop
  patch -Np1 -i ../chromium-vesktop.patch

  # Link to system tools required by the build
  mkdir -p third_party/node/linux/node-linux-x64/bin
  ln -sfn /usr/bin/node third_party/node/linux/node-linux-x64/bin/
  mkdir -p third_party/jdk/current/bin
  ln -sfn /usr/bin/java third_party/jdk/current/bin/
  ln -sfn /usr/bin/clang-format buildtools/linux64

  # Electron specific fixes
  patch -Np1 -i "${srcdir}/jinja-python-3.10.patch" -d "third_party/electron_node/tools/inspector_protocol/jinja2"
  patch -Np1 -i "${srcdir}/use-system-libraries-in-node.patch"
  # patch -Np1 -i "${srcdir}/default_app-icon.patch"  # Icon from .desktop file

  # Allow building against system libraries in official builds
  echo "Patching Chromium for using system libraries..."
  sed -i 's/OFFICIAL_BUILD/GOOGLE_CHROME_BUILD/' \
    tools/generate_shim_headers/generate_shim_headers.py

  # Remove bundled libraries for which we will use the system copies; this
  # *should* do what the remove_bundled_libraries.py script does, with the
  # added benefit of not having to list all the remaining libraries
  local _lib
  for _lib in ${_unwanted_bundled_libs[@]}; do
    find "third_party/$_lib" -type f \
      \! -path "third_party/$_lib/chromium/*" \
      \! -path "third_party/$_lib/google/*" \
      \! -path "third_party/harfbuzz-ng/utils/hb_scoped.h" \
        \! -regex '.*\.\(gn\|gni\|isolate\)' \
        -delete
  done

  ./build/linux/unbundle/replace_gn_files.py \
    --system-libraries "${!_system_libs[@]}"
}

build() {
  cd src

  export CC=clang
  export CXX=clang++
  export AR=ar
  export NM=nm

  local _flags=(
    'custom_toolchain="//build/toolchain/linux/unbundle:default"'
    'host_toolchain="//build/toolchain/linux/unbundle:default"'
    'is_official_build=true' # implies is_cfi=true on x86_64
    'symbol_level=0' # sufficient for backtraces on x86(_64)
    'treat_warnings_as_errors=false'
    'disable_fieldtrial_testing_config=true'
    'blink_enable_generated_code_formatting=false'
    'ffmpeg_branding="Chrome"'
    'proprietary_codecs=true'
    'rtc_use_pipewire=true'
    'link_pulseaudio=true'
    'use_custom_libcxx=true' # https://github.com/llvm/llvm-project/issues/61705
    'use_sysroot=false'
    'use_system_libffi=true'
    'enable_hangout_services_extension=true'
    'enable_widevine=false'
    'enable_nacl=false'
  )

  if [[ -n ${_system_libs[icu]+set} ]]; then
    _flags+=('icu_use_data_file=false')
  fi

  local _clang_version=$(
    clang --version | grep -m1 version | sed 's/.* \([0-9]\+\).*/\1/')

  _flags+=(
    'clang_base_path="/usr"'
    'clang_use_chrome_plugins=false'
    "clang_version=\"$_clang_version\""
    'chrome_pgo_phase=2'
  )

  # Allow the use of nightly features with stable Rust compiler
  # https://github.com/ungoogled-software/ungoogled-chromium/pull/2696#issuecomment-1918173198
  export RUSTC_BOOTSTRAP=1

  _flags+=(
    'rust_sysroot_absolute="/usr"'
    'rust_bindgen_root="/usr"'
    "rustc_version=\"$(rustc --version)\""
  )

  # Facilitate deterministic builds (taken from build/config/compiler/BUILD.gn)
  CFLAGS+='   -Wno-builtin-macro-redefined'
  CXXFLAGS+=' -Wno-builtin-macro-redefined'
  CPPFLAGS+=' -D__DATE__=  -D__TIME__=  -D__TIMESTAMP__='

  # Do not warn about unknown warning options
  CFLAGS+='   -Wno-unknown-warning-option'
  CXXFLAGS+=' -Wno-unknown-warning-option'

  # Let Chromium set its own symbol level
  CFLAGS=${CFLAGS/-g }
  CXXFLAGS=${CXXFLAGS/-g }

  # https://github.com/ungoogled-software/ungoogled-chromium-archlinux/issues/123
  CFLAGS=${CFLAGS/-fexceptions}
  CFLAGS=${CFLAGS/-fcf-protection}
  CXXFLAGS=${CXXFLAGS/-fexceptions}
  CXXFLAGS=${CXXFLAGS/-fcf-protection}

  # This appears to cause random segfaults when combined with ThinLTO
  # https://bugs.archlinux.org/task/73518
  CFLAGS=${CFLAGS/-fstack-clash-protection}
  CXXFLAGS=${CXXFLAGS/-fstack-clash-protection}

  # https://crbug.com/957519#c122
  CXXFLAGS=${CXXFLAGS/-Wp,-D_GLIBCXX_ASSERTIONS}

  export CHROMIUM_BUILDTOOLS_PATH="${PWD}/buildtools"
  gn gen out/Release \
      --args="import(\"//electron/build/args/release.gn\") ${_flags[*]}"
  ninja -C out/Release electron electron_dist_zip
  # ninja -C out/Release third_party/electron_node:headers
}

package() {
  install -dm755 "${pkgdir:?}/usr/lib/${pkgname}"
  bsdtar -xf src/out/Release/dist.zip -C "${pkgdir}/usr/lib/${pkgname}"

  chmod u+s "${pkgdir}/usr/lib/${pkgname}/chrome-sandbox"

  install -dm755 "${pkgdir}/usr/share/licenses/${pkgname}"
  for l in "${pkgdir}/usr/lib/${pkgname}"/{LICENSE,LICENSES.chromium.html}; do
    ln -s  \
      "$(realpath --relative-to="${pkgdir}/usr/share/licenses/${pkgname}" "${l}")" \
      "${pkgdir}/usr/share/licenses/${pkgname}"
  done

  install -Dm755 "${srcdir}/electron-launcher.sh" \
    "${pkgdir}/usr/bin/${pkgname}"

  # Install .desktop and icon file (see default_app-icon.patch)
  install -Dm644 electron.desktop \
    "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -Dm644 src/electron/default_app/icon.png \
          "${pkgdir}/usr/share/pixmaps/${pkgname}.png"  # hicolor has no 1024x1024
}
