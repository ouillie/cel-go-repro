Run:

```
bazel build ...
```

All is good.

Uncomment lines 24-27 in MODULE.bazel.

Run:

```
$ bazel build ...
Computing main repo mapping:
Loading:
Loading: 0 packages loaded
bazel: Entering directory `/private/var/tmp/_bazel_jward/27df4ae6b5564cd962492ba6fb2041bc/execroot/_main/'
Analyzing: 2 targets (2 packages loaded, 0 targets configured)
Analyzing: 2 targets (2 packages loaded, 0 targets configured)

INFO: Analyzed 2 targets (195 packages loaded, 10482 targets configured).
INFO: Found 2 targets...
bazel: Leaving directory `/private/var/tmp/_bazel_jward/27df4ae6b5564cd962492ba6fb2041bc/execroot/_main/'
INFO: Elapsed time: 1.424s, Critical Path: 0.17s
INFO: 1 process: 138 action cache hit, 1 internal.
INFO: Build completed successfully, 1 total action
~/src/github.com/jarreds/cel-go-repro $ git branch -M main
~/src/github.com/jarreds/cel-go-repro $ git remote add origin git@github.com:jarreds/cel-go-repro.git
~/src/github.com/jarreds/cel-go-repro $ git push -u origin main
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 10 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (10/10), 3.31 KiB | 3.31 MiB/s, done.
Total 10 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
To github.com:jarreds/cel-go-repro.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
~/src/github.com/jarreds/cel-go-repro $ git push -u origin main
branch 'main' set up to track 'origin/main'.
Everything up-to-date
~/src/github.com/jarreds/cel-go-repro $ bazel build ...
Computing main repo mapping:
Computing main repo mapping:
Loading:
Loading: 0 packages loaded
Loading: 0 packages loaded
DEBUG: /private/var/tmp/_bazel_jward/27df4ae6b5564cd962492ba6fb2041bc/external/gazelle+/internal/bzlmod/go_deps.bzl:607:40:
Mismatch between versions requested for Go module cel.dev/expr:

  bazel_dep version (MODULE.bazel): 0.15.0 (as "cel-spec")
  Go module version (go.mod):       0.23.1

Either ensure that you have

  bazel_dep(module_name = "cel-spec", version = "0.23.1")

in your MODULE.bazel file or downgrade the Go module version via

  bazel run @rules_go//go -- get cel.dev/expr@v0.15.0

bazel: Entering directory `/private/var/tmp/_bazel_jward/27df4ae6b5564cd962492ba6fb2041bc/execroot/_main/'
Analyzing: 2 targets (2 packages loaded, 0 targets configured)
Analyzing: 2 targets (2 packages loaded, 0 targets configured)

ERROR: no such package '@@[unknown repo 'dev_cel_expr' requested from @@gazelle++go_deps+com_github_google_cel_go]//': The repository '@@[unknown repo 'dev_cel_expr' requested from @@gazelle++go_deps+com_github_google_cel_go]' could not be resolved: No repository visible as '@dev_cel_expr' from repository '@@gazelle++go_deps+com_github_google_cel_go'
ERROR: /private/var/tmp/_bazel_jward/27df4ae6b5564cd962492ba6fb2041bc/external/gazelle++go_deps+com_github_google_cel_go/cel/BUILD.bazel:7:11: no such package '@@[unknown repo 'dev_cel_expr' requested from @@gazelle++go_deps+com_github_google_cel_go]//': The repository '@@[unknown repo 'dev_cel_expr' requested from @@gazelle++go_deps+com_github_google_cel_go]' could not be resolved: No repository visible as '@dev_cel_expr' from repository '@@gazelle++go_deps+com_github_google_cel_go' and referenced by '@@gazelle++go_deps+com_github_google_cel_go//cel:go_default_library'
bazel: Leaving directory `/private/var/tmp/_bazel_jward/27df4ae6b5564cd962492ba6fb2041bc/execroot/_main/'
ERROR: Analysis of target '//cel-test:cel-test' failed; build aborted: Analysis failed
INFO: Elapsed time: 3.577s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
ERROR: Build did NOT complete successfully
FAILED:
```
