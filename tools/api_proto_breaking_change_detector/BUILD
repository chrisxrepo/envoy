load("@rules_python//python:defs.bzl", "py_binary", "py_library", "py_test")

licenses(["notice"])  # Apache 2

py_binary(
    name = "detector",
    srcs = [
        "detector.py",
    ],
    data = [
        "@com_github_bufbuild_buf//:buf",
        "@envoy_api_canonical//:proto_breaking_change_detector_buf_config",
    ],
    main = "detector.py",
    tags = ["manual"],
    deps = [
        ":buf_utils",
        ":detector_errors",
        "//tools:run_command",
    ],
)

py_library(
    name = "buf_utils",
    srcs = [
        "buf_utils.py",
    ],
    deps = [
        ":detector_errors",
        "//tools/base:utils",
    ],
)

py_library(
    name = "detector_errors",
    srcs = [
        "detector_errors.py",
    ],
)

py_test(
    name = "detector_test",
    srcs = ["detector_test.py"],
    data = [
        "//tools/testdata/api_proto_breaking_change_detector:proto_breaking_change_detector_testdata",
    ],
    main = "detector_test.py",
    python_version = "PY3",
    srcs_version = "PY3",
    tags = ["manual"],
    deps = [
        ":detector",
        "//tools:run_command",
        "@rules_python//python/runfiles",
    ],
)
