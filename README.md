DQN for Breakout
================

This project is modified from https://github.com/wetliu/dqn_pytorch based on my
opinionated styles of coding.

And here are some pre-trained weights that you can play with:
- [model_weights_a](https://github.com/lukeluocn/dqn-breakout/releases/download/v0.0.0/model_weights_a)
- [model_weights_b](https://github.com/lukeluocn/dqn-breakout/releases/download/v0.0.0/model_weights_b)

将基础DQN修改为Dueling_DQN
将该模型放到自己的PC上执行时会遇到几个需要修改的地方:

在vendor/atari_wrappers.py中:

需要将第54行的
```
noops = self.unwrapped.np_random.randint(1, self.noop_max + 1)  # pylint: disable=E1101
```
修改为
```
noops = self.unwrapped.np_random.integers(1, self.noop_max + 1)  # pylint: disable=E1101
```
将第58行的
```
obs, _, done, _ = self.env.step(self.noop_action)
```
修改为
```
obs, _, done, _ ,_= self.env.step(self.noop_action)
```
将第141行的
```
obs, reward, done, info = self.env.step(action)
```
修改为
```
obs, reward, done, info,_ = self.env.step(action)
```
