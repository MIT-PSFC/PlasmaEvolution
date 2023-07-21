# MIT Gang Text
First activate the included venv (I was initially using conda, but conda on engaging has been sad):
```
python3 -m venv env
source env/bin/activate
python3 -m pip install -r requirements.txt
```
To build instances of `TensorDataset`, I made the script `build_datsets.py` that takes in `*.h5` files in `in_dir` and outputs `*.pt` to `out_dir`. An example usage is:

```
python3 build_datasets.py --in_dir ~/Scratch/protected_data/abbate_2021/ --out_dir ~/Scratch/protected_data/abbate_2021/
```
You may or may not run out of space on Engaging. If you do, maybe build the `*.pt` files elsewhere and then copy them over to Engaging.

# Original Text
This repo trains and analyzes neural nets for predicting how a tokamak (fusion reactor) plasma will evolve in time given an initial condition and user-specified actuator trajectories. It is a (pytorch-based) cleanup of the (tensorflow-based) [plasma-profile-predictor](https://github.com/PlasmaControl/plasma-profile-predictor), which was described in our [2021 Nuclear Fusion paper](https://doi.org/10.1088/1741-4326/abe08d).

In train.py point the data_filename to an h5 file generated from [data-fetching repo](https://github.com/PlasmaControl/data-fetching), then run test case with
    python train.py

For pytorch environment setup on PPPL/Princeton's Traverse cluster along with a ton of other helpful info and examples, see [researchcomputing.princeton.edu](https://researchcomputing.princeton.edu/pytorch). h5py is also required for reading the h5 dataset. As of February 2023, I personally use
    module load anaconda3/2022.5
    conda create --name torch --channel "https://opence.mit.edu/#/" "pytorch==1.12*=cuda11*" torchvision
    conda install -c anaconda h5py
    conda activate torch

And of course reload anaconda and activate this environment every time you go to run the code.