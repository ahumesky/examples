load("@rules_shell//shell:sh_binary.bzl", "sh_binary")
load(":execute.bzl", "concat")

concat(
    name = "sh",
    out = "page.html",
    chunks = [
        "header.html",
        "body.html",
        "footer.html",
    ],
    merge_tool = select({
        "//conditions:default": ":merge_on_linux",
        "on_linux": ":merge_on_linux",
        "on_windows": ":merge_on_windows.bat",
    }),
)

# This target is used by the shell rule.
sh_binary(
    name = "merge_on_linux",
    srcs = ["merge.sh"],
)

sh_binary(
    name = "merge_on_windows.bat",
    srcs = ["merge.bat"],
)

config_setting(
    name = "on_linux",
    constraint_values = [
        "@platforms//os:linux",
    ],
)

config_setting(
    name = "on_windows",
    constraint_values = [
        "@platforms//os:windows",
    ],
)
