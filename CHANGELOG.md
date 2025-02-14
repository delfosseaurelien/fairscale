# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## NEXT - TBD
### Added
### Fixed

## [0.3.3] - 2021-04-1
### Added
- FSDP: changed auto\_wrap\_bn utility function so that single FSDP group is optional ([#556](https://github.com/facebookresearch/fairscale/pull/556))
- FSDP: optimizer state load/save ([#537](https://github.com/facebookresearch/fairscale/pull/537))
- FSDP: fix weight init when using apply() ([#543](https://github.com/facebookresearch/fairscale/pull/543))
- Multiprocess Pipe: retired old implementation
- Experimental: xpipe

### Fixed
- ShardedDDP deferred init ([#558](https://github.com/facebookresearch/fairscale/pull/558))

## [0.3.2] - 2021-03-18
### Added
- Experimental: Add spectrain support ([#372](https://github.com/facebookresearch/fairscale/issues/372))
- FSDP: enabled pytorch SyncBN (no asserting) ([#527](https://github.com/facebookresearch/fairscale/issues/527))
- FSDP: added auto\_wrap\_bn utility function ([#531](https://github.com/facebookresearch/fairscale/pull/531))

### Fixed
- OSS: fix a compatibily problem with lightning wrt optimizer state dict ([#510](https://github.com/facebookresearch/fairscale/issues/510))
- FSDP: fixed a bug when part of autograd graph is traversed multiple times in mixed precision mode ([#513](https://github.com/facebookresearch/fairscale/pull/513))

## [0.3.1] - 2021-03-09
### Added
- FSDP docs ([#455](https://github.com/facebookresearch/fairscale/issues/455))
- enable\_wrap and auto\_wrap APIs ([#446](https://github.com/facebookresearch/fairscale/issues/446))
- Added experimental.nn.OffloadModel API for training large models on a single GPU.([#432](https://github.com/facebookresearch/fairscale/issues/432))

### Fixed
- OSS: fix a broken state dict when using non contiguous param groups
- Several SDP fixes around performance and corner cases
- Many FSDP fixes
- AdaScale & SDP/FSDP test added but not officially supported

## [0.3.0] - 2021-02-22
### Added
- FullyShardedDataParallel (FSDP) ([#413](https://github.com/facebookresearch/fairscale/issues/413))
- ShardedDDP fp16 grad reduction option ([#402](https://github.com/facebookresearch/fairscale/issues/402))
- Expose experimental algorithms within the pip package ([#410](https://github.com/facebookresearch/fairscale/pull/410))

### Fixed
- Catch corner case when the model is too small with respect to the world size, and shards are empty ([#406](https://github.com/facebookresearch/fairscale/pull/406))
- Memory leak in checkpoint\_wrapper ([#412](https://github.com/facebookresearch/fairscale/pull/412))

## [0.1.7] - 2021-02-19
### Fixed
- ShardedDDP and OSS handle model trainability changes during training ([#369](https://github.com/facebookresearch/fairscale/issues/369))
- ShardedDDP state dict load/save bug ([#386](https://github.com/facebookresearch/fairscale/issues/386))
- ShardedDDP handle train/eval modes ([#393](https://github.com/facebookresearch/fairscale/issues/393))
- AdaScale handling custom scaling factors ([#401](https://github.com/facebookresearch/fairscale/issues/401))

### Added
- ShardedDDP manual reduce option for checkpointing ([#389](https://github.com/facebookresearch/fairscale/issues/389))

## [0.1.6] - 2021-02-10
### Added
- Checkpointing model wrapper (#376)
- Faster OSS, flatbuffers (#371)
- Small speedup in OSS clipgradnorm (#363)

### Fixed
- Bug in ShardedDDP with 0.1.5 depending the init (KeyError / OSS)
- Much refactoring in Pipe (#357, #358, #360, #362, #370, #373)
- Better pip integration / resident pytorch (#375)

## [0.1.5] - 2021-02-03
### Added
- Pytorch compatibility for OSS checkpoints (#310)
- Elastic checkpoints for OSS, world size can vary in between save and loads (#310)
- Tensor views for OSS bucketing, reduced CPU use (#300)
- Bucket calls in ShardedDDP, for faster inter node communications (#327)
- FlattenParamWrapper, which flattens module parameters into a single tensor seamlessly (#317)
- AMPnet experimental support (#304)

### Fixed
- ShardedDDP properly handles device changes via `.to()` (#353)
- Add a new interface for AdaScale, AdaScaleWrapper, which makes it compatible with OSS (#347)


## [0.1.4] - 2021-01-07
### Fixed
- Missing cu files in the pip package


## [0.1.3] - 2021-01-04
### Fixed
- Release numbering within python and from pypi

## [0.1.2] - 2021-01-04
### Added
- AdaScale:
  . Added gradient accumulation feature (#202)
  . Added support of torch.lr_scheduler (#229)
  . Added support for add_param_groups (#266)
  . Added support for scale != world_size (#266)

### Fixed
- AdaScale: smoothing factor value fixed when using gradient accumulation (#235)
- Pipe: documentation on balancing functions (#243)
- ShardedDDP: handle typical NLP models
- ShardedDDP: better partitioning when finetuning


## [0.1.1] - 2020-12-01
### Fixed
- make sure pip package includes header files (#221)

## [0.1.0] - 2020-12-01
### Added
- ShardedDataParallel with autoreduce (#157)
- cpu support for Pipe (#188)
- ShardedOptim: Distributed Grad Scaler (for torch AMP)  (#182)
- OSS-aware clip grads, bridge sharded states (#167)
- oss: add rank_local_state_dict staticmethod (#174)
- support for PyTorch 1.7.0 (#171)
- Add implementation of AdaScale (#139)

### Fixed
- pip package install (#196, #200)

## [0.0.3] - 2020-10-14
### Added
- multi-process pipe

### Fixed
- multiple OSS fixes
- MegaTron+OSS DDP fix

## [0.0.2] - 2020-08-28
### Added
- add ddp that works with oss with reduce() not all_reduce() (#19)
- support for PyTorch v1.6
- add mixed precision Adam (#40)
- Adam optimizer state scaling (#44)

### Fixed
- properly restore a sharded optim state (#39)
- OSS restore state to proper device (#46)
- optim/oss: support optimizers with additional step kwargs (#53)
- optim/oss: fix state cast (#56)
- fix eval for oss_ddp (#55)
- optim/oss: work correctly with LRScheduler (#58)

## [0.0.1] - 2020-07-31
- Initial release.
