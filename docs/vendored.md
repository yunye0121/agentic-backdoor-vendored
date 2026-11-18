# Vendored dependencies

This mirror **vendors** the third-party repositories directly in-tree instead
of using Git submodules, so a plain `git clone` contains everything; no
`git submodule` command and no access to GitHub is needed. Each vendored tree
is an unmodified checkout of the commit below (the local patches in
[patches/](../patches/README.md) are still applied at setup time by
`scripts/setup/apply_patches.sh`). Each dependency retains its own license and
attribution.

| Path | Upstream | Commit |
| --- | --- | --- |
| `Megatron-Bridge` | https://github.com/NVIDIA-NeMo/Megatron-Bridge.git | `b9d90ceae3ce8f050649376edeb2e22e8171a8b1` |
| `Megatron-Bridge/3rdparty/Megatron-LM` | https://github.com/NVIDIA/Megatron-LM.git | `faced512869f130ae4c5d1b4779c3f7fd52b74ed` |
| `Megatron-LM` | https://github.com/NVIDIA/Megatron-LM.git | `5eb20b89ac228ee3aa19f79d85e075b29f1e3ac1` |
| `terminal-bench-rl` | https://github.com/Danau5tin/terminal-bench-rl.git | `d25baf0d6eb4738a4fed12cad20a7f535348f133` |
| `terminal-bench-rl/external/rllm` | https://github.com/agentica-project/rllm.git | `2ce8e5494c16c5b8286eccb09fc7008a71a1a4b7` |
| `terminal-bench-rl/external/rllm/verl` | https://github.com/agentica-project/verl | `1a398434995c8cea19e841ca30b5a3738cc9fc15` |

Nested submodules (rLLM and VERL inside `terminal-bench-rl`, and the
Megatron-LM copy inside `Megatron-Bridge/3rdparty`) are vendored as well. Their
own `.gitmodules` files are kept for reference only; Git ignores them outside
the repository root.

To refresh a dependency, replace its directory with a clean checkout of the
new commit (delete that checkout's `.git`), update this table, and commit.

Continue with the environment setup scripts in the main README. The
`src/agent_core` and `src/tbench_rllm` symlinks resolve into the vendored
`terminal-bench-rl` tree. Model weights, generated corpora and credentials are
not part of the repository.
