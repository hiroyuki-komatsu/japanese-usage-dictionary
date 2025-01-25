# Japanese usage dictionary

This project manages dictionary entries to distingush Japanese homonym words (同音異義語).

The data is designed for Japanese input especially for the [Mozc](https://github.com/google/mozc/) project, but the data is applicable for other purposes.

## usage_dict.txt

Main data. The format is TSV. The fields are

1. reading of the word (i.e. あう)
2. literal token of the word (i.e. 会う)
3. part-of-speech (i.e. 五段・ワ行促音便)
4. definition of the word (i.e. 人にあう。「友達と会う」)

```
あう	会う	五段・ワ行促音便	人にあう。「友達と会う」
あう	合う	五段・ワ行促音便	ぴったりあう。「息が合う」「答が合う」
```

## BUILD / MODULE.bazel

Rules for Bazel.

Example for your project's MODULE.bazel:

```
# Japanese Usage Dictionary
bazel_dep(
    name = "ja_usage_dict",
    repo_name = "ja_usage_dict",
)
git_override(
    module_name = "ja_usage_dict",
    remote = "https://github.com/hiroyuki-komatsu/japanese-usage-dictionary",
    tag = "2025-01-25",
)

## Use the local file with local_path_override instead of git_overide.
# local_path_override(
#     module_name = "ja_usage_dict",
#     path = "third_party/japanese_usage_dictionary",
# )
```
