# DeepFRI

### DeepFRI: Structure-based protein function prediction using graph convolutional networks

[Paper](https://www.nature.com/articles/s41467-021-23303-9#Sec1) [Github](https://github.com/flatironinstitute/DeepFRI)

DeepFRI: a Graph Convolutional Network for predicting protein functions by leveraging sequence features extracted from a protein language model and protein structures. 

Class activation mapping allows function predictions at an unprecedented resolution, allowing site-specific annotations at the residue-level in an automated manner. ==This is interesting==

Core pipeline:

这个方法将蛋白质结构转化为 contact map 作为输入，可能损失很多的信息？不过使用了图网络倒是可以避免，但是很可能难以learn到global的性质

还是把这个作为Benchmark吧



## Installation

```bash
git clone https://github.com/flatironinstitute/DeepFRI.git


module load miniconda3
conda create -n DeepFRI python=3.7

pip install numpy==1.18.5 tensorflow-gpu==2.3.1 networkx==2.4 scikit-learn==0.23.1 biopython==1.76

wget [准备训练好的模型]


```





```bash
# predicting functions of a protein from a PDB file
python predict.py -pdb ./examples/pdb_files/1S3P-A.pdb -ont mf -v

# predicting functions of a protein from a directory with PDB files
python predict.py --pdb_dir ./examples/pdb_files -ont mf --saliency --use_backprop

```

