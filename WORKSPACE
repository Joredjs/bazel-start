#Definicion del workspace
workspace(
	name = "test-workspace"
)

#Carga de la libreria http_archive para extraer archivos
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

#Descarga las reglas de js (las reglas de nodejs @rules_nodejs están sin mantenimiento)
http_archive(
    name = "aspect_rules_js",
    sha256 = "686d5b345592c1958b4aea24049d935ada11b83ae5538658d22b84b353cfbb1e",
    strip_prefix = "rules_js-1.13.1",
    url = "https://github.com/aspect-build/rules_js/archive/refs/tags/v1.13.1.tar.gz",
)

#Carga de la libreria	rules_js_dependencies
load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")
rules_js_dependencies()

#Carga de la regla nodejs_register_toolchains desde @rules_nodejs
load("@rules_nodejs//nodejs:repositories.bzl", "DEFAULT_NODE_VERSION", "nodejs_register_toolchains")
nodejs_register_toolchains(
    name = "nodejs",
    node_version = DEFAULT_NODE_VERSION,
)

#carga de la regla npm_translate_lock
load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")
npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
    verify_node_modules_ignored = "//:.bazelignore",
)

load("@npm//:repositories.bzl", "npm_repositories")
npm_repositories()