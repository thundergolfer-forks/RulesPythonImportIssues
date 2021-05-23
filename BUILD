load("@rules_python//python:defs.bzl", "py_library", "py_test")
load("@pip//:requirements.bzl", "requirement")

py_library(
  name = "dataflow",
  srcs = ["dataflow.py"],
  deps = [
    requirement("google-auth"),
    requirement("google-auth-httplib2"),
    requirement("google-api-core"),
    requirement("google-api-python-client"),
    requirement("python-dateutil"),
  ],
  visibility = [
    "//crestone/luigi:__subpackages__",
  ],
)

py_test(
  name = "dataflow_test",
  srcs = ["dataflow_test.py"],
  deps = [
    ":dataflow",
    requirement("absl-py"),
  ],
)