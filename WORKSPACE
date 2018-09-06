workspace(name = "toktok")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("//tools/workspace:github.bzl", "github_archive")

git_repository(
    name = "bazel_skylib",
    remote = "https://github.com/bazelbuild/bazel-skylib.git",
    tag = "0.5.0",
)

# Skydoc
# =========================================================

github_archive(
    name = "io_bazel_skydoc",
    repo = "bazelbuild/skydoc",
    sha256 = "2885adbe581576b2b3ec906eeebc3692e45386651502411284c50979add0fa89",
    version = "0.1.4",
)

load("@io_bazel_skydoc//skylark:skylark.bzl", "skydoc_repositories")

skydoc_repositories()

# Haskell
# =========================================================

github_archive(
    name = "io_tweag_rules_haskell",
    repo = "tweag/rules_haskell",
    sha256 = "854099bec683161b2b6da7e84f29d5f19d095b44fb936332664dcf7b6e9517f1",
    version = "35195f2005226b76e65bed31f1dd815810f94634",
)

load("@io_tweag_rules_haskell//haskell:ghc_bindist.bzl", "ghc_bindist")
load("//third_party/haskell:haskell.bzl", "new_cabal_package")

# This repository rule creates @ghc repository.
ghc_bindist(
    name = "ghc",
)

register_toolchains("//:ghc")

new_local_repository(
    name = "haskell_base",
    build_file = "third_party/haskell/BUILD.bazel",
    path = "/usr",
)
