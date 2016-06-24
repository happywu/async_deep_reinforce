# async_deep_reinforce

Asynchronous deep reinforcement learning

## About

An attempt to repdroduce Google Deep Mind's paper "Asynchronous Methods for Deep Reinforcement Learning."

http://arxiv.org/abs/1602.01783

Asynchronous Advantage Actor-Critic (A3C) method for playing "Atari Pong" is implemented with TensorFlow.

Learning result movment after 26 hour is like this.

[![Learning result after 26 hour](http://narr.jp/private/miyoshi/deep_learning/a3c_preview_image.jpg)](https://youtu.be/ZU71YdAedZs)

Any advice or suggestion is strongly welcomed in issues thread.

https://github.com/miyosuda/async_deep_reinforce/issues/1

## How to build

First we need to build multi thread ready version of Arcade Learning Enviroment.
I made some modification to it to run it on multi thread enviroment.

    $ git clone https://github.com/miyosuda/Arcade-Learning-Environment.git
    $ cd Arcade-Learning-Environment
    $ cmake -DUSE_SDL=ON -DUSE_RLGLUE=OFF -DBUILD_EXAMPLES=ON .
    $ make -j 4
	
    $ pip install .

I recommend to install it on VirtualEnv environment.

## How to run

To train,

    $python a3c.py

To display the result with game play,

    $python a3c_disp.py

## Using GPU
To enable gpu, change "USE_GPU" flag in "constants.py".

When running with 8 parallel game environemts, speeds of GPU (GTX980Ti) and CPU(Core i7 6700) were like this.

|type | speed             |
|-----|-------------------|
| GPU | 821 steps per sec |
| CPU | 472 steps per sec |


## Result
Score plot of local threads of pong in 24h (70.9 million global steps) was like this. (with GTX980Ti)

![scores of local threads](https://github.com/miyosuda/async_deep_reinforce/blob/master/docs/graph_24h.png)

Scores are not averaged using global network unlike the original paper.

## References

This project uses setting written in muupan's wiki [muuupan/async-rl] (https://github.com/muupan/async-rl/wiki)


## Acknowledgements

- [@aravindsrinivas](https://github.com/aravindsrinivas) for providing information for some of the hyper parameters.

