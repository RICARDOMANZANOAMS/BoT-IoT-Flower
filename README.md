# BoT-IoT-Flower


----------------INSTALL-------------------



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

GPU 
pip install torch==2.0.1+cu118 torchvision==0.15.2+cu118 torchaudio==2.0.2+cu118 --index-url https://download.pytorch.org/whl/cu118
pip instal pandas
pip install -U scikit-learn

---------------RUN-----------------------------

To run the program check the following functions


strategy = fl.server.strategy.FedAvg(fraction_fit=1, # let's sample 10% of the client each round to do local training
                                      fraction_evaluate=1, # after each round, let's sample 20% of the clients to asses how well the global model is doing
                                      min_available_clients=4, # total number of clients available in the experiment
                                      evaluate_fn=get_evalulate_fn(testloader)) # a callback to a function that the strategy can execute to evaluate the state of the global model on a centralised dataset


history = fl.simulation.start_simulation(
    client_fn=client_fn_callback, # a callback to construct a client
    num_clients=5, # total number of clients in the experiment
    config=fl.server.ServerConfig(num_rounds=100), # let's run for 10 rounds
    strategy=strategy,# the strategy that will orchestrate the whole FL pipeline
)


min_available_clients in strategy should be less that num_clients in history
fraction_fit in strategy should be 1 to train with all the datasets
fraction_evaluate in strategy should be 1 to evaluate in all the datasets











The following are the versions used to start Flower in the local machine
