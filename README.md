# build conda env
conda create -n csi python==3.10 -y
conda activate csi

# install the package
pip install -e .

# install other packages

pip install torch==2.3.1

pip install pytorch-lightning==1.9.1

pip install torchvision==0.18.1

pip install omegaconf==2.3.0

pip install timm==1.0.15

# data preparation
run: 

python data_process/down_load_data.py

if one has no futu API, plz direcitly unzip HK_5M.zip


# main result

train:

python main_candlestick.py -n main_result --base configs/HK_5M_r_v7.yaml -t --root_dir logs --gpus [your gpu here]

test:

python test_tools/compute_ic_on_val.py
