package(default_visibility = ["//visibility:public"])
load("@org_tensorflow_tensorboard//tensorboard/defs:web.bzl", "tf_web_library")
load("@org_tensorflow_tensorboard//tensorboard/defs:vulcanize.bzl", "tensorboard_html_binary")

tf_web_library(
    name = "visualizations",
    srcs = [
        "visualizations.html",
    ],
    path = "/facets",
    deps = [
        "//facets_overview/components/facets_overview",
        "@org_tensorflow_tensorboard//tensorboard/components:polymer",
    ],
)

tensorboard_html_binary(
    name = "facets",
    compile = True,
    input_path = "/facets/visualizations.html",
    output_path = "/all/visualizations.html",
    deps = [":visualizations"],
)

genrule(
    name = "facets_jupyter",
    srcs = [":facets"],
    outs = ["facets-jupyter.html"],
    cmd = "sed 's|<!doctype html>|<!doctype html><script>define=undefined</script>|' $(location :facets) > $@",
)