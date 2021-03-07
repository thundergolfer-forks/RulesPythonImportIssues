# The Workspace file for the Crestone project. It currently makes use of only
# the Python rules: https://github.com/bazelbuild/rules_python

workspace(name = "Crestone")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_python",
    url = "https://github.com/bazelbuild/rules_python/releases/download/0.1.0/rules_python-0.1.0.tar.gz",
    sha256 = "b6d46438523a3ec0f3cead544190ee13223a52f6a6765a29eae7b7cc24cc83a0",
)

load("@rules_python//python:pip.bzl", "pip_install")
pip_install(
    requirements = "//crestone:requirements.txt",
)

# Subpar allows creation of self-hosting Python executables:
# https://github.com/google/subpar
git_repository(
    name = "subpar",
    remote = "https://github.com/google/subpar",
    commit = "35bb9f0092f71ea56b742a520602da9b3638a24f",
    shallow_since = "1557863961 -0400",
)

# Package rules
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "rules_pkg",
    urls = [
        "https://github.com/bazelbuild/rules_pkg/releases/download/0.2.6-1/rules_pkg-0.2.6.tar.gz",
        "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/0.2.6/rules_pkg-0.2.6.tar.gz",
    ],
    sha256 = "aeca78988341a2ee1ba097641056d168320ecc51372ef7ff8e64b139516a4937",
)
load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")
rules_pkg_dependencies()

git_repository(
    name = "com_google_protobuf",
    remote = "https://github.com/JoshuaCrestone/protobuf.git",
    commit = "35101a5387872d0310c3c65962503e7da823a8f2",
    shallow_since = "1602648557 -0600",
)
load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")
protobuf_deps()

# Docker rules
# Download the rules_docker repository at release v0.14.4
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "1698624e878b0607052ae6131aa216d45ebb63871ec497f26c67455b34119c80",
    strip_prefix = "rules_docker-0.15.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.15.0/rules_docker-v0.15.0.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//python:image.bzl",
    _py_image_repos = "repositories",
)

_py_image_repos()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

# Base images for Docker containers.
container_pull(
  name = "scipy_notebook",
  registry = "index.docker.io",
  repository = "jupyter/scipy-notebook",
  # 'tag' is also supported, but digest is encouraged for reproducibility.
  digest = "sha256:8e3c844d40f54e4280d045e6ce9e2bda345ae660a27585e74e181a69cb51c1b4",
)

container_pull(
  name = "luigi",
  registry = "index.docker.io",
  repository = "spotify/luigi",
  digest = "sha256:00fcd3a1bebff4dfac78c380d2e837bf4c7780277d30a800b8621f9547309afc",
)

container_pull(
  name = "bazel",
  registry = "l.gcr.io",
  repository = "google/bazel",
  digest = "sha256:ace9881e6e9c5d48b5fd637321361aeffe54000265894a65f7d818dc1065bd80"
)

container_pull(
  name = "tensorflow_latest_gpu_jupyter",
  registry = "index.docker.io",
  repository = "tensorflow/tensorflow",
  digest = "sha256:c3b4e83edf14b282902c80e0ef245115736ce4c91eabc39c93f51ca56508e504",
)