load("@rules_cc//cc:defs.bzl", "cc_binary")


cc_binary(
    name = "main",
    srcs = ["main.cc"],
    copts = [ 
        '-fopenmp',
    ],
)

extra_action(
    name = "extractor",
    cmd = ("/home/werider/kythe_b1/kythe-v0.0.52/extractors/bazel_cxx_extractor " +
           "$(EXTRA_ACTION_FILE) $(output $(ACTION_ID).cxx.kzip) $(location :vnames.json)"),
    data = [":vnames.json"],
    out_templates = ["$(ACTION_ID).cxx.kzip"],
)

action_listener(
    name = "extract_cxx",
    extra_actions = [":extractor"],
    mnemonics = ["CppCompile"],
    visibility = ["//visibility:public"],
)