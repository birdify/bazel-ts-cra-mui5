workspace(name = "bazel_ts_cra_mui5")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "3ceb1e5b5dcad5fa2ad8870a20201cfbb9c9c63cac4055c9ab370034c765297f",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.3.0/rules_nodejs-5.3.0.tar.gz"],
)

load("@build_bazel_rules_nodejs//:repositories.bzl", "build_bazel_rules_nodejs_dependencies")

build_bazel_rules_nodejs_dependencies()

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    # Name this npm so that Bazel Label references look like @npm//package
    name = "npm",
    data = ["//:patches/jest-haste-map+26.6.2.patch"],
    exports_directories_only = True,
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)
