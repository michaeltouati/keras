# Description:
#   Contains Keras integration tests that verify with other TF high level APIs.

load("@org_keras//keras:keras.bzl", "cuda_py_test")
load("@org_keras//keras:keras.bzl", "tf_py_test")  # buildifier: disable=same-origin-load
load("@org_keras//keras:keras.bzl", "tpu_py_test")
load("@org_keras//keras:keras.bzl", "distribute_py_test")

package(
    default_visibility = [
        "//keras:friends",
        "//third_party/tensorflow/tools/pip_package:__pkg__",
    ],
    licenses = ["notice"],
)

tf_py_test(
    name = "forwardprop_test",
    srcs = ["forwardprop_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_absl_installed",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

tf_py_test(
    name = "function_test",
    srcs = ["function_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

tf_py_test(
    name = "gradients_test",
    srcs = ["gradients_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

cuda_py_test(
    name = "saved_model_test",
    srcs = ["saved_model_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_absl_installed",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

tf_py_test(
    name = "legacy_rnn_test",  # Remove this target in when TF 1 is deprecated.
    srcs = ["legacy_rnn_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

tf_py_test(
    name = "module_test",
    srcs = ["module_test.py"],
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

tf_py_test(
    name = "vectorized_map_test",
    srcs = ["vectorized_map_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

cuda_py_test(
    name = "gradient_checkpoint_test",
    srcs = ["gradient_checkpoint_test.py"],
    python_version = "PY3",
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

# cuda_py_test(
#     name = "central_storage_strategy_test",
#     srcs = ["central_storage_strategy_test.py"],
#     python_version = "PY3",
#     tags = [
#         "multi_and_single_gpu",
#         "no_windows_gpu",  # TODO(b/130551176)
#     ],
#     deps = [
#         "//:expect_absl_installed",
#         "//:expect_tensorflow_installed",
#         "//third_party/tensorflow/python/distribute:combinations",
#         "//third_party/tensorflow/python/distribute:strategy_combinations",
#         "//third_party/tensorflow/python/keras/utils:kpl_test_utils",
#     ],
# )

tpu_py_test(
    name = "tpu_strategy_test",
    srcs = ["tpu_strategy_test.py"],
    disable_experimental = True,
    disable_mlir_bridge = False,
    python_version = "PY3",
    tags = ["no_oss"],
    deps = [
        "//:expect_absl_installed",
        "//:expect_tensorflow_installed",
    ],
)

tf_py_test(
    name = "multi_worker_tutorial_test",
    srcs = ["multi_worker_tutorial_test.py"],
    python_version = "PY3",
    shard_count = 6,
    tags = [
        "no_windows",  # TODO(b/183102726)
        "noasan",  # TODO(b/156029134)
        "nomac",  # TODO(b/182567880)
        "nomsan",  # TODO(b/156029134)
        "notsan",  # TODO(b/156029134)
    ],
    deps = [
        "//:expect_absl_installed",
        "//:expect_portpicker_installed",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

distribute_py_test(
    name = "parameter_server_keras_preprocessing_test",
    srcs = ["parameter_server_keras_preprocessing_test.py"],
    python_version = "PY3",
    shard_count = 4,  # TODO(b/184290570): Investigate why only 1 shard times out.
    tags = [
        "multi_and_single_gpu",
        "no_oss",  # TODO(b/194935930): Flaky test
        "nomultivm",  # TODO(b/170502145)
    ],
    deps = [
        "//:expect_absl_installed",
        "//:expect_portpicker_installed",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

distribute_py_test(
    name = "distributed_training_test",
    srcs = ["distributed_training_test.py"],
    python_version = "PY3",
    shard_count = 50,
    tags = [
        "multi_gpu",
        "no_oss",  # TODO(b/183640564): Re-enable
        "no_rocm",
        "noasan",  # TODO(b/184542721)
        "nomsan",  # TODO(b/184542721)
        "nomultivm",  # TODO(b/170502145)
        "notsan",  # TODO(b/184542721)
    ],
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

distribute_py_test(
    name = "mwms_multi_process_runner_test",
    srcs = ["mwms_multi_process_runner_test.py"],
    python_version = "PY3",
    tags = [
        "multi_gpu",
        "no_rocm",
        "noasan",  # TODO(b/184542721)
        "nomsan",  # TODO(b/184542721)
        "nomultivm",  # TODO(b/170502145)
        "notpu",
        "notsan",  # TODO(b/184542721)
    ],
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

py_library(
    name = "preprocessing_test_utils",
    srcs = ["preprocessing_test_utils.py"],
    srcs_version = "PY3",
    deps = ["//:expect_tensorflow_installed"],
)

distribute_py_test(
    name = "preprocessing_applied_in_dataset_creator_test",
    srcs = ["preprocessing_applied_in_dataset_creator_test.py"],
    python_version = "PY3",
    shard_count = 50,
    tags = [
        "multi_gpu",
        "no_oss",  # TODO(b/183640564): Re-enable
        "no_rocm",
        "noasan",  # TODO(b/184542721)
        "nomsan",  # TODO(b/184542721)
        "nomultivm",  # TODO(b/170502145)
        "notsan",  # TODO(b/184542721)
    ],
    deps = [
        ":preprocessing_test_utils",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

distribute_py_test(
    name = "preprocessing_applied_in_dataset_test",
    srcs = ["preprocessing_applied_in_dataset_test.py"],
    python_version = "PY3",
    shard_count = 50,
    tags = [
        "multi_gpu",
        "no_oss",  # TODO(b/183640564): Re-enable
        "no_rocm",
        "noasan",  # TODO(b/184542721)
        "nomsan",  # TODO(b/184542721)
        "nomultivm",  # TODO(b/170502145)
        "notsan",  # TODO(b/184542721)
    ],
    deps = [
        ":preprocessing_test_utils",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

distribute_py_test(
    name = "preprocessing_applied_in_model_test",
    srcs = ["preprocessing_applied_in_model_test.py"],
    python_version = "PY3",
    shard_count = 50,
    tags = [
        "multi_gpu",
        "no_oss",  # TODO(b/183640564): Re-enable
        "no_rocm",
        "noasan",  # TODO(b/184542721)
        "nomsan",  # TODO(b/184542721)
        "nomultivm",  # TODO(b/170502145)
        "notsan",  # TODO(b/184542721)
    ],
    deps = [
        ":preprocessing_test_utils",
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)

distribute_py_test(
    name = "parameter_server_custom_training_loop_test",
    srcs = ["parameter_server_custom_training_loop_test.py"],
    python_version = "PY3",
    tags = [
        "multi_gpu",
        "no_oss",  # TODO(b/183640564): Re-enable
        "no_rocm",
        "noasan",  # TODO(b/184542721)
        "nomsan",  # TODO(b/184542721)
        "nomultivm",  # TODO(b/170502145)
        "notsan",  # TODO(b/184542721)
    ],
    deps = [
        "//:expect_tensorflow_installed",
        "//keras/api:keras_api",
    ],
)
