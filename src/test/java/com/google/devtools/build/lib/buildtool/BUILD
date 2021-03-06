load("@rules_java//java:defs.bzl", "java_library", "java_test")

package(
    default_testonly = 1,
    default_visibility = ["//src:__subpackages__"],
)

filegroup(
    name = "srcs",
    testonly = 0,
    srcs = glob(["**"]),
    visibility = ["//src/test/java/com/google/devtools/build/lib:__pkg__"],
)

java_library(
    name = "testutil",
    srcs = glob(["util/*.java"]),
    deps = [
        "//src/main/java/com/google/devtools/build/lib:bazel-main",
        "//src/main/java/com/google/devtools/build/lib:bazel/BazelRepositoryModule",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:build-request-options",
        "//src/main/java/com/google/devtools/build/lib:command-utils",
        "//src/main/java/com/google/devtools/build/lib:detailed_exit_code",
        "//src/main/java/com/google/devtools/build/lib:events",
        "//src/main/java/com/google/devtools/build/lib:exitcode-external",
        "//src/main/java/com/google/devtools/build/lib:keep-going-option",
        "//src/main/java/com/google/devtools/build/lib:loading-phase-threads-option",
        "//src/main/java/com/google/devtools/build/lib:logging-util",
        "//src/main/java/com/google/devtools/build/lib:packages-internal",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/buildeventstream",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/collect/nestedset",
        "//src/main/java/com/google/devtools/build/lib/exec/local:options",
        "//src/main/java/com/google/devtools/build/lib/includescanning",
        "//src/main/java/com/google/devtools/build/lib/network:connectivity_status",
        "//src/main/java/com/google/devtools/build/lib/network:noop_connectivity",
        "//src/main/java/com/google/devtools/build/lib/profiler",
        "//src/main/java/com/google/devtools/build/lib/sandbox",
        "//src/main/java/com/google/devtools/build/lib/shell",
        "//src/main/java/com/google/devtools/build/lib/standalone",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/build/lib/vfs:output_service",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/common/options:invocation_policy",
        "//src/main/java/com/google/devtools/common/options:options_internal",
        "//src/main/protobuf:invocation_policy_java_proto",
        "//src/test/java/com/google/devtools/build/lib:actions_testutil",
        "//src/test/java/com/google/devtools/build/lib:analysis_testutil",
        "//src/test/java/com/google/devtools/build/lib:foundations_testutil",
        "//src/test/java/com/google/devtools/build/lib:integration_testutil",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//src/test/java/com/google/devtools/build/lib/skyframe:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "BuildtoolTests",
    srcs = [
        "JobsConverterTest.java",
        "SymlinkForestTest.java",
    ],
    test_class = "com.google.devtools.build.lib.AllTests",
    runtime_deps = ["//src/test/java/com/google/devtools/build/lib:test_runner"],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:build-request-options",
        "//src/main/java/com/google/devtools/build/lib:packages-internal",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/actions:localhost_capacity",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/build/lib/vfs/inmemoryfs",
        "//src/main/java/com/google/devtools/common/options:options_internal",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "ActionListenerIntegrationTest",
    srcs = ["ActionListenerIntegrationTest.java"],
    tags = [
        "no_windows",
        # TODO(laszlocsomor): remove "manual" after BuildIntegrationTestCase works with Bazel.
        "manual",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/collect/nestedset",
        "//src/main/java/com/google/devtools/build/lib/rules/java:java-compilation",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/common/options",
        "//src/main/protobuf:extra_actions_base_java_proto",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "BogusExecutionTimeTest",
    srcs = ["BogusExecutionTimeTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "CompileAfterOptionChangeTest",
    srcs = ["CompileAfterOptionChangeTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "CompileOneDependencyIntegrationTest",
    srcs = ["CompileOneDependencyIntegrationTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:events",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "ContextProviderInitializationTest",
    srcs = ["ContextProviderInitializationTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "CorruptedActionCacheTest",
    srcs = ["CorruptedActionCacheTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "DanglingSymlinkTest",
    srcs = ["DanglingSymlinkTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "DirectoryArtifactWarningTest",
    srcs = ["DirectoryArtifactWarningTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "EditDuringBuildTest",
    srcs = ["EditDuringBuildTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "EnvironmentRestrictedBuildTest",
    srcs = ["EnvironmentRestrictedBuildTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "ExecutionPhaseContainingPackageLookupTest",
    srcs = ["ExecutionPhaseContainingPackageLookupTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":IoHookTestCase",
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "GenQueryIntegrationTest",
    srcs = ["GenQueryIntegrationTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "IncludeValidationTest",
    srcs = ["IncludeValidationTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "InconsistentFilesystemTest",
    srcs = ["InconsistentFilesystemTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:unix",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "LabelCrossesPackageBoundaryTest",
    srcs = ["LabelCrossesPackageBoundaryTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "MiscAnalysisTest",
    srcs = ["MiscAnalysisTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:events",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:analysis_testutil",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:guava-testlib",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "MissingInputActionTest",
    srcs = ["MissingInputActionTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "ModifyBuildFileTest",
    srcs = ["ModifyBuildFileTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "NoOutputActionTest",
    srcs = ["NoOutputActionTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "OutputArtifactConflictTest",
    srcs = ["OutputArtifactConflictTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "PackageGroupIntegrationTest",
    srcs = ["PackageGroupIntegrationTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/test/java/com/google/devtools/build/lib:analysis_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "ProgressReportingTest",
    srcs = ["ProgressReportingTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:events",
        "//src/main/java/com/google/devtools/build/lib:unix",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:analysis_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "QueryIntegrationTest",
    srcs = ["QueryIntegrationTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:events",
        "//src/main/java/com/google/devtools/build/lib:keep-going-option",
        "//src/main/java/com/google/devtools/build/lib:packages-internal",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib/query2/common:abstract-blaze-query-env",
        "//src/main/java/com/google/devtools/build/lib/query2/engine",
        "//src/main/java/com/google/devtools/build/lib/query2/query/output",
        "//src/main/java/com/google/devtools/common/options",
        "//src/main/protobuf:build_java_proto",
        "//src/main/protobuf:invocation_policy_java_proto",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "SymlinkDependencyAnalysisTest",
    srcs = ["SymlinkDependencyAnalysisTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:packages_testutil",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "TransitiveDataDependencyTest",
    srcs = ["TransitiveDataDependencyTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "BuildResultTestCase",
    srcs = ["BuildResultTestCase.java"],
    shard_count = 4,
    tags = [
        "manual",
        "no_windows",
    ],
    test_class = "com.google.devtools.build.lib.AllTests",
    runtime_deps = ["//src/test/java/com/google/devtools/build/lib:test_runner"],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_library(
    name = "CustomRealFilesystemBuildIntegrationTestCase",
    srcs = ["CustomRealFilesystemBuildIntegrationTestCase.java"],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:unix",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_library(
    name = "IoHookTestCase",
    srcs = ["IoHookTestCase.java"],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:unix",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/test/java/com/google/devtools/build/lib:testutil",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "AqueryBuildToolTest",
    srcs = ["AqueryBuildToolTest.java"],
    tags = [
        "manual",
        "no_windows",
    ],
    deps = [
        ":testutil",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib/query2",
        "//src/main/java/com/google/devtools/build/lib/query2/engine",
        "//src/main/java/com/google/devtools/common/options",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

test_suite(
    name = "windows_tests",
    tags = [
        "-no_windows",
        "-slow",
    ],
    visibility = ["//visibility:private"],
)

test_suite(
    name = "all_windows_tests",
    tests = [
        ":windows_tests",
    ],
    visibility = ["//src/test/java/com/google/devtools/build/lib:__pkg__"],
)
