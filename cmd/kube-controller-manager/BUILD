package(default_visibility = ["//visibility:public"])

load(
    "@io_bazel_rules_go//go:def.bzl",
    "go_binary",
    "go_library",
)
load("//pkg/version:def.bzl", "version_x_defs")

go_binary(
    name = "kube-controller-manager",
    gc_linkopts = [
        "-linkmode",
        "external",
        "-extldflags",
        "-static",
    ],
    importpath = "k8s.io/kubernetes/cmd/kube-controller-manager",
    library = ":go_default_library",
    x_defs = version_x_defs(),
)

go_library(
    name = "go_default_library",
    srcs = ["controller-manager.go"],
    importpath = "k8s.io/kubernetes/cmd/kube-controller-manager",
    deps = [
        "//cmd/kube-controller-manager/app:go_default_library",
        "//cmd/kube-controller-manager/app/options:go_default_library",
        "//pkg/client/metrics/prometheus:go_default_library",
        "//pkg/util/reflector/prometheus:go_default_library",
        "//pkg/util/workqueue/prometheus:go_default_library",
        "//pkg/version/prometheus:go_default_library",
        "//pkg/version/verflag:go_default_library",
        "//vendor/github.com/spf13/pflag:go_default_library",
        "//vendor/k8s.io/apiserver/pkg/util/flag:go_default_library",
        "//vendor/k8s.io/apiserver/pkg/util/logs:go_default_library",
    ],
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [
        ":package-srcs",
        "//cmd/kube-controller-manager/app:all-srcs",
    ],
    tags = ["automanaged"],
)
