# Sentry-Audio-Backups

本项目用于备份 **Lenovo Chromebook Sentry (Kabylake)** 在 Linux (如 MX Linux) 环境下的音频修复配置文件与原厂固件。

这些文件提取自官方 Recovery 镜像：`chromeos_15393.58.0_sentry_recovery_stable-channel_mp-v2`。

## 🛠 核心硬件参数
- **CPU Platform:** Intel Kabylake (SST Architecture)
- **Audio Codec:** DA7219 (Headphone Jack)
- **Speaker Amp:** MAX98357A
- **Driver Module:** `snd-soc-kbl_da7219_max98357a`

## 📂 文件说明
- `/firmware`: 存放 DSP 固件（包含 `dfw_sst.bin` 和 `dsp_fw_kbl_v*.bin`）。
- `/ucm`: 存放 ALSA Use Case Manager 配置文件。

## 🚀 关键修复指令 (备忘)
如果在 Linux 下识别到声卡但无声，需手动开启核心路由开关：

```bash
# 开启核心媒体流路由 (总闸)
amixer -c sklnau8825max cset name='codec0_out mo media0_in mi Switch' on

# 开启扬声器物理开关
amixer -c sklnau8825max cset name='Spk Switch' on
