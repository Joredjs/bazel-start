bazel_dep(name = "aspect_rules_js", version = "1.13.1")

npm = use_extension("@aspect_rules_js//npm:extensions.bzl", "npm", dev_dependency = True)

npm.npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
)
use_repo(npm, "npm")

load("@npm//:defs.bzl", "npm_link_all_packages")
npm_link_all_packages()