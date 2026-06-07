# HW2-math

# HW2工程數學：拉普拉斯反轉換

本專案記錄了拉普拉斯反轉換題目的詳細拆解與求解步驟。

---

## 題目 (4)：用拉普拉斯反轉換求解方程

**題目：**
求以下函數的反轉換：

$$
\mathcal{L}^{-1} \left[ \frac{s+3}{(s+1)^2(s+2)} \right]
$$

### Step 1：部分分式展開 (Partial Fraction Expansion)
因為分母含有重複實根 $(s+1)^2$ 與單純實根 $(s+2)$，可假設展開式為：

$$
\frac{s+3}{(s+1)^2(s+2)} = \frac{A}{s+1} + \frac{B}{(s+1)^2} + \frac{C}{s+2}
$$

兩邊同乘以 $(s+1)^2(s+2)$ 以消去分母：

$$
s+3 = A(s+1)(s+2) + B(s+2) + C(s+1)^2
$$

使用**代入法**求解未知係數：

### 📌 令 s = -1 
$$
-1 + 3 = B(-1 + 2)
$$
$$
2 = B \cdot 1 \implies B = 2
$$

### 📌 令 s = -2
$$
-2 + 3 = C(-2 + 1)^2
$$
$$
1 = C(-1)^2 \implies C = 1
$$

### 📌 令 s = 0（代入已求得的 B = 2, C = 1）
$$
0 + 3 = A(1)(2) + 2(2) + 1(1)^2
$$
$$
3 = 2A + 4 + 1
$$
$$
3 = 2A + 5 \implies 2A = -2 \implies A = -1
$$

因此，部分分式展開結果為：

$$
\frac{s+3}{(s+1)^2(s+2)} = \frac{-1}{s+1} + \frac{2}{(s+1)^2} + \frac{1}{s+2}
$$

### Step 2：進行拉普拉斯反轉換
利用常用反轉換公式：

$$
\mathcal{L}^{-1} \left[ \frac{1}{s-a} \right] = e^{at}
$$

$$
\mathcal{L}^{-1} \left[ \frac{1}{(s-a)^2} \right] = t e^{at}
$$

將各項單獨進行反轉換：

$$
\mathcal{L}^{-1} \left[ \frac{-1}{s+1} \right] = -e^{-t}
$$

$$
\mathcal{L}^{-1} \left[ \frac{2}{(s+1)^2} \right] = 2t e^{-t}
$$

$$
\mathcal{L}^{-1} \left[ \frac{1}{s+2} \right] = e^{-2t}
$$

### 題目 (4) 最終答案

$$
f(t) = -e^{-t} + 2te^{-t} + e^{-2t} \quad (t \ge 0)
$$
## 題目 (6)：求 $f(t) = t e^{-5t}$ 之傅立葉分析

> 💡 **說明：** 題目內文提及「求傅立葉級數 (Fourier series)」，但該函數為非週期性的衰減訊號，通常適用於「傅立葉變換 (Fourier Transform)」。以下採用**傅立葉變換**進行標準求解（假設 $t > 0$，即 $f(t) = t e^{-5t} u(t)$）。

### Step 1：基礎變換公式
已知標準指數衰減訊號的傅立葉變換為：

$$
\mathcal{F}\{e^{-at} u(t)\} = \frac{1}{a + j\omega}
$$

本題中 $a = 5$，故：

$$
\mathcal{F}\{e^{-5t} u(t)\} = \frac{1}{5 + j\omega}
$$

### Step 2：利用頻率微分性質
根據傅立葉變換的時域乘上 $t$ 的性質：

$$
\mathcal{F}\{t \cdot f(t)\} = j \frac{d}{d\omega} F(\omega)
$$

將 Step 1 的結果代入該性質中：

$$
F(\omega) = j \frac{d}{d\omega} \left( \frac{1}{5 + j\omega} \right)
$$

### Step 3：微分計算
對 $\omega$ 進行連鎖律微分：

$$
\frac{d}{d\omega} (5 + j\omega)^{-1} = -(5 + j\omega)^{-2} \cdot \frac{d}{d\omega}(5 + j\omega) = \frac{-j}{(5 + j\omega)^2}
$$

將外部的 $j$ 乘入：

$$
F(\omega) = j \cdot \left[ \frac{-j}{(5 + j\omega)^2} \right] = \frac{-j^2}{(5 + j\omega)^2}
$$

因 $j^2 = -1$，故 $-j^2 = 1$。

### 題目 (6) 最終答案

$$
F(\omega) = \frac{1}{(5 + j\omega)^2}
$$
