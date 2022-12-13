# Defines the name
workspace(name = "bazel_with_typescript")

# Allows us to download rules via the internet
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "c2ad51299792d5af3b258f1dd71b3b57eff9424c2e1797d9c1d65717d95da03a",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.7.3/rules_nodejs-5.7.3.tar.gz"],
)

# this loads our bazel rules for nodejs
load("@build_bazel_rules_nodejs//:repositories.bzl", "build_bazel_rules_nodejs_dependencies")

# this calls the rules we just loaded
build_bazel_rules_nodejs_dependencies()

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    name = "npm",
    exports_directories_only = False,
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

load("@npm//@bazel/protractor:package.bzl", "npm_bazel_protractor_dependencies")

npm_bazel_protractor_dependencies()
