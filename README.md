# BoT-IoT-Flower


To install Flower locally is necessary to install conda. 

conda create --name flower-federated python=3.10.12
conda activate flower-federated
conda install ipykernel
python -m ipykernel install --user --name=flower-federated
pip install jupyter
pip install -q flwr[simulation] torch torchvision
pip install pydantic==1.10.11

Verify that the version of pydantic os 1.10.11 and ray 2.5.1. It appears an error if the version of pydantic is greater. I had to downgrade to solve the error

Strategy to see what is the correct version for each package. I run in google colab and pip list the versions. 






The following are the versions used to start Flower in the local machine
