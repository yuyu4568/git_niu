# 高频电子线路 · 第 2 章 高频基础电路笔记

> 依据课堂录音《“指定方向录音 1”-转文本结果》整理，已校正语音识别误差，并补充公式推导与扩展。配套移动端页面见同目录 `index.html`。

## 0. 课程定位

- **研究对象**：无线电通信系统中与高频信号处理有关的基本单元电路。
- **重点设备**：发送设备、接收设备。
- **高频范围**：3～30 MHz（短波段）。
- **典型单元电路**：高频小信号放大器、高频功率放大器、选频回路/滤波器。
- **公共基础**：LC 串并联谐振回路、阻抗变换电路、匹配网络、滤波器。

无线电通信系统五部分：输入变换器 → 发送设备 → 传输信道 → 接收设备 → 输出变换器。

## 1. 无源集总元件模型

### 1.1 电感线圈

串联等效：

$$
Z_L=R_0+j\omega L,\qquad Q_0=\frac{\omega L}{R_0},\qquad \varphi=\arctan\frac{\omega L}{R_0}
$$

并联等效：

$$
Y_L=G_0+\frac{1}{j\omega L}=G_0-j\frac{1}{\omega L}
$$

### 1.2 电容

串联等效：

$$
Z_C=R_0+\frac{1}{j\omega C}=R_0-j\frac{1}{\omega C},\qquad Q_0=\frac{1}{\omega C R_0}
$$

并联等效：

$$
Y_C=G_0+j\omega C
$$

**重点**：\(Q\) 是储能与耗能之比。串联支路电流相等，故 \(Q=\omega L/R_0\)；并联支路电压相等，故公式中电阻在分子。电容的 \(Q_0\) 可达几千到几万，工程上常视为无损元件。

## 2. LC 串联谐振回路

### 2.1 电路与阻抗

$$
Z=R+j\left(\omega L-\frac{1}{\omega C}\right)
$$

$$
|Z|=\sqrt{R^2+\left(\omega L-\frac{1}{\omega C}\right)^2}
$$

空载时 \(R=R_0\)；有载时 \(R=R_0+R_L\)。

### 2.2 谐振频率

令虚部为零：

$$
\omega_0=\frac{1}{\sqrt{LC}},\qquad f_0=\frac{1}{2\pi\sqrt{LC}}
$$

### 2.3 品质因数

$$
Q_0=\frac{\omega_0 L}{R_0}=\frac{1}{\omega_0 C R_0}
$$

$$
Q_L=\frac{\omega_0 L}{R_0+R_L}=\frac{1}{\omega_0 C(R_0+R_L)}
$$

### 2.4 特性

$$
|Z|=R\sqrt{1+Q^2\left(\frac{\omega}{\omega_0}-\frac{\omega_0}{\omega}\right)^2}
$$

$$
\varphi=\arctan\left[Q\left(\frac{\omega}{\omega_0}-\frac{\omega_0}{\omega}\right)\right]
$$

- \(\omega=\omega_0\)：阻抗最小，纯阻性，电流最大。
- \(\omega>\omega_0\)：感性，\(\varphi>0\)。
- \(\omega<\omega_0\)：容性，\(\varphi<0\)。

## 3. LC 并联谐振回路

### 3.1 两种形式

- 形式 A：\(R_0\) 与 \(L\) 串联后再与 \(C\) 并联。
- 形式 B：\(G_0\)、\(L\)、\(C\) 三支路并联。

### 3.2 导纳与谐振频率（形式 A）

$$
Y=\frac{R_0}{R_0^2+(\omega L)^2}
  +j\left[\omega C-\frac{\omega L}{R_0^2+(\omega L)^2}\right]
$$

令虚部为零：

$$
\omega_p=\sqrt{\frac{1}{LC}-\frac{R_0^2}{L^2}}
=\omega_0\sqrt{1-\frac{1}{Q_0^2}}
$$

当 \(Q_0\gg1\)，\(\omega_p\approx\omega_0\)。

### 3.3 谐振电阻与 Q

$$
R_p=\frac{R_0^2+(\omega L)^2}{R_0}
    =R_0(1+Q_0^2)\approx Q_0^2R_0
$$

有载并联品质因数：

$$
Q_L=\frac{R}{\omega_0 L}=\omega_0 C R,\qquad
\frac{1}{R}=\frac{1}{R_0}+\frac{1}{R_L}
$$

### 3.4 特性

$$
|Z|=\frac{R}{\sqrt{1+Q^2\left(\frac{\omega}{\omega_0}-\frac{\omega_0}{\omega}\right)^2}}
$$

$$
\varphi=-\arctan\left[Q\left(\frac{\omega}{\omega_0}-\frac{\omega_0}{\omega}\right)\right]
$$

- \(\omega=\omega_0\)：阻抗最大，纯阻性。
- \(\omega>\omega_0\)：容性，\(\varphi<0\)。
- \(\omega<\omega_0\)：感性，\(\varphi>0\)。

## 4. 串并联阻抗等效变换

同频率下，串联 \(R_1+jX_1\) 与并联 \(R_2\parallel jX_2\) 端口等效。设 \(Q=R_2/X_2\)：

$$
R_1=\frac{R_2}{1+Q^2},\qquad
X_1=\frac{Q^2}{1+Q^2}X_2
$$

$$
R_2=(1+Q^2)R_1,\qquad
X_2=\left(1+\frac{1}{Q^2}\right)X_1
$$

高 Q 时：

$$
R_2\approx Q^2R_1,\qquad X_2\approx X_1
$$

## 5. 耦合连接与接入系数

定义 \(p=U_2/U_1\)。折合到一次侧：

$$
R_L'=\frac{R_L}{p^2},\qquad
X_L'=\frac{X_L}{p^2},\qquad
L_L'=\frac{L_L}{p^2}
$$

$$
U_1'=\frac{U_2}{p},\qquad
I_1'=pI_2
$$

- 变压器耦合：\(p=N_2/N_1\)。
- 自耦变压器：\(p=N_2/(N_1+N_2)\)。
- 电容分压：\(p=C_1/(C_1+C_2)\)。

## 6. 功率传输与匹配网络

高频功率放大器必须进行输出匹配，避免反射、功率损耗和功放损坏。

最大功率传输条件为共轭匹配：

$$
Z_{in}=Z_S^*
$$

即 \(R_{in}=R_S\)、\(X_{in}=-X_S\)。纯电阻源时 \(R_L=R_S\)，负载获得最大功率，但效率只有 50%。

滤波器/选频网络用于抑制带外干扰。LC 谐振回路本质上是带通选频网络；高性能接收机还可用多级回路、晶体/陶瓷/SAW 滤波器改善矩形系数。

## 7. 公式速查

| 物理量 | 公式 | 说明 |
|---|---|---|
| 谐振频率 | \(f_0=\frac{1}{2\pi\sqrt{LC}}\) | 理想 LC |
| 电感 Q | \(Q_0=\omega L/R_0\) | 串联 |
| 电容 Q | \(Q_0=1/(\omega C R_0)\) | 串联 |
| 串联谐振阻抗 | \(R\sqrt{1+Q^2(\omega/\omega_0-\omega_0/\omega)^2}\) | \(\omega_0\) 处最小 |
| 并联谐振阻抗 | \(R/\sqrt{1+Q^2(\omega/\omega_0-\omega_0/\omega)^2}\) | \(\omega_0\) 处最大 |
| 串并联变换 | \(R_2=(1+Q^2)R_1\) | 高 Q 时 \(R_2\approx Q^2R_1\) |
| 接入系数 | \(R_L'=R_L/p^2\) | \(p=U_2/U_1\) |
| 最大功率 | \(Z_{in}=Z_S^*\) | 共轭匹配 |

## 自测

1. 串联谐振和并联谐振在 \(\omega>\omega_0\) 时分别呈什么性质？
2. 为什么并联有损谐振频率略低于 \(1/\sqrt{LC}\)？
3. 已知 \(N_1:N_2=4:1\)、\(R_L=50\,\Omega\)，求折合到一次侧的 \(R_L'\)。
4. 共轭匹配与最高效率是否等价？为什么？
