# Workaround for using conda on BeeGFS system

The current version of BeeGFS used for `/home` and `/work` on the Draco and Ara Cluster has a known problem with conda: BeeGFS, a parallel cluster file system, does not support hard-links between files in different directories.
A workaround is to shift to `/vast` an let conda install its environments there. This can be realized with the following three lines (replace `$USER` with your URZ-ID):

```
[login1: ~] mkdir -p /vast/$USER/.conda/{envs,pkgs} 
[login1: ~] conda config --prepend envs_dirs /vast/$USER/.conda/envs 
[login1: ~] conda config --prepend pkgs_dirs /vast/$USER/.conda/pkgs
```
