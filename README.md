# Workaround for using conda on BeeGFS system

The version of BeeGFS used for `/home` and `/work` on the Draco Cluster has a known problem with conda: BeeGFS, a parallel cluster file system, does not support hard-links between files in different directories (see [Release Notes v7.4.0](https://doc.beegfs.io/7.4.0/release_notes.html)
A workaround is to shift to `/vast` an let conda install its environments there. This can be realized with the following three lines (replace `$USER` with your URZ-ID):

```
[login1: ~] mkdir -p /vast/$USER/.conda/{envs,pkgs} 
[login1: ~] conda config --prepend envs_dirs /vast/$USER/.conda/envs 
[login1: ~] conda config --prepend pkgs_dirs /vast/$USER/.conda/pkgs
```
