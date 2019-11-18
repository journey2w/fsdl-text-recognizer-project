# Full Stack Deep Learning Labs

Welcome!

Project developed during lab sessions of the [Full Stack Deep Learning Bootcamp](https://fullstackdeeplearning.com).

- We will build a handwriting recognition system from scratch, and deploy it as a web service.
- Uses Keras, but designed to be modular, hackable, and scalable
- Provides code for training models in parallel and store evaluation in Weights & Biases
- We will set up continuous integration system for our codebase, which will check functionality of code and evaluate the model about to be deployed.
- We will package up the prediction system as a REST API, deployable as a Docker container.
- We will deploy the prediction system as a serverless function to Amazon Lambda.
- Lastly, we will set up monitoring that alerts us when the incoming data distribution changes.

# SR Jupyterlab에서 하려면

1. https://jupyterlab.sel.sr-cloud.com/ 에 접속한다.
2. 가입 및 소스코드 다운로드
    - 가입은 자동으로 되는 것 같고 소스코드는 git clone 등으로 하시면 됩니다.

**참고사항**

1. 매번 다른 VM을 할당하는 것 같습니다
    - 따라서 apt-get으로 설치하는 패키지를 매번 설치해야 한다고 함.
    - 그런데 저는 저장되는 것으로 보여서.. 이건 상황이 따라 유연하게 :)
2. 기존에는 pipenv로 의존성을 설치했는데 poetry로 대체했습니다.
    - 3.6을 사용하도록 하고 있는데 저희 VM이 3.7을 지원해서 차이를 맞춰줘야 했고
    - 제가 최근에 관심을 가지고 보고 있던 패키지 메니저라서 그냥 썻습니다.
    - pipenv를 사용하셔도 되지만.. 잘 안되더라구요

### 설치 방법

apt-get으로 필수 패키지 몇개를 설치합니다.

```bash
$ sudo apt-get install -y gcc libglib2.0-0
```

poetry를 설치합니다.

```bash
$ pip install poetry
```

poetry를 활용해서 의존성을 설치합니다.

```bash
$ poetry install
```

설치된 의존성을 사용할 수 있도록 python을 가상 환경으로 전환합니다.

- 이 때부터 python과 pip registry가 virtualenv로 대체됩니다.

```sh
$ poetry shell
```

이 레포지토리의 명령어들은 대부분 현재 디렉토리가 `PYTHONPATH`에 지정되어 있다고 가정하여 작성되어 있습니다. 따라서 이를 설정합니다

```sh
echo "export PYTHONPATH=." > ~/.bashrc
export PYTHONPATH=.
```

준비가 완료되었습니다.
각 디렉토리에서 예제를 실행하시면 됩니다 :)

만약 의존성 패키지가 없어 학습이 실패한다면 아래 `poetry add <Package Name>`으로 추가하시면 됩니다.

- poetry 관련 가이드는 아래 링크를 참고해주세요
- https://poetry.eustace.io/docs/cli/#install

tasks 디렉토리에 있는 shell 파일에 `pipenv run` 이라는 prefix가 붙어 있어 빌드가 실패합니다. 이것만 지우고 다시 실행하시면 됩니다.

```diff
-pipenv run python training/prepare_experiments.py training/experiments/sample.json
+python training/prepare_experiments.py training/experiments/sample.json
```

## Schedule for the Spring 2019 Bootcamp

- First session (90 min)
  - Overview of the labs. (15 min)
  - Get set up. (10 min)
  - Lab 1 (20 min): Project structure. 
  - Lab 2 (25 min): Introduce EMNIST. Training code details. Train & evaluate character prediction baselines.
  - Lab 3 (20 min): Introduce EMNIST Lines. Overview of model architecture. Train our model on EMNIST Lines.
- Second session (60 min)
  - Lab 4 (20 min): Weights & Biases + parallel experiments.
  - Lab 5 (40 min): IAM Lines and experimentation time (launch a bunch of experiments, leave running overnight in a shared W&B).
- Third session (90 min)
  - Review results from the class on W&B
  - Lab 6 (60 min) line detection task
  - Lab 7 (30 min) data labeling
    - Go through data versioning and even have a little labeling interface for fresh data that they generated on the first day
- Fourth session (75 min)
  - Lab 8 (15 min) continuous integration
  - Lab 8 (60 min) web deployment

# Setup


## 1. Set up your machine

- In the live class we used a sponsored instance of Jupyter Hub to run experiments. 
- You can use Google Colab to run your projects on a notebook in the cloud.
- We recommend Weights & Biases for experiment tracking. It's a free tool for students, and you can learn more at wandb.com.


## 2. Check out the repo

You should already have the repo in your home directory. Go into it and make sure you have the latest.

```sh
cd fsdl-text-recognizer-project
git pull origin master
```

If not, open a shell in your JupyterLab instance and run

```sh
git clone https://github.com/gradescope/fsdl-text-recognizer-project.git
cd fsdl-text-recognizer-project
```


## 3. Set up the Python environment

Run

```sh
pipenv install --dev
```

From now on, precede commands with `pipenv run` to make sure they use the correct
environment.

# Ready

Now you should be setup for the labs. The instructions for each lab are in readme files in their folders.

You will notice that there are solutions for all the labs right here in the repo, too.
If you get stuck, you are welcome to take a look!
