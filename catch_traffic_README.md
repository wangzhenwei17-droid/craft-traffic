# catch_traffic.ipynb 使用说明（Binder / GitHub）

这个文档用于说明 `catch_traffic.ipynb` 在 GitHub + Binder 上如何一键打开与运行，以及所需的依赖（`requirements.txt`）。

---

## 1. 建议的 requirements.txt

将下面内容保存为仓库根目录的 `requirements.txt`：

```txt
numpy
pandas
matplotlib
scapy
```

> 可选：如果你希望更稳定，也可以写最低版本（不强制）：
>
> ```txt
> numpy>=1.24
> pandas>=1.5
> matplotlib>=3.6
> scapy>=2.5
> ```

---

## 2. Binder 一键打开链接（推荐分享给别人用）

把下面链接里的 `<USER>` 和 `<REPO>` 替换成你的 GitHub 用户名和仓库名即可：

```text
https://mybinder.org/v2/gh/<USER>/<REPO>/main?urlpath=lab/tree/catch_traffic.ipynb
```

如果你的默认分支不是 `main`，把 `main` 改成 `master` 或实际分支名。

---

## 3. README 徽章（可选）

把下面这段粘贴到仓库 `README.md`，别人点徽章就能打开 Notebook：

```md
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/<USER>/<REPO>/main?urlpath=lab/tree/catch_traffic.ipynb)
```

---

## 4. 运行注意事项（非常重要）

### 4.1 关于 scapy 实时抓包（sniff）
如果 Notebook 里用到了 `scapy.sniff()` 做“实时抓包”，在 Binder 这类云端环境中**经常会抓不到包**，原因通常是：
- 权限限制（需要更高权限）
- 网络隔离（看不到你本地网卡的真实流量）

这不是依赖问题，即使装好了 `scapy` 也可能无法实时抓包。

### 4.2 更稳定的演示方式：读取 pcap 文件
更推荐把抓到的包保存成 `*.pcap` 文件，然后在 Notebook 里读取它做分析/可视化：
- 把 `sample.pcap` 放到仓库（例如 `data/sample.pcap`）
- Notebook 读取并解析 pcap（这样 Binder 上也能复现）

如果你愿意，我也可以帮你把 Notebook 改成“优先读取 pcap，抓不到再提示”的形式，保证别人点开就能跑通主要流程。

---

## 5. 最小目录结构建议

```text
my-binder-notebook/
  catch_traffic.ipynb
  requirements.txt
  README.md
  data/
    sample.pcap        # 可选：用于演示的 pcap
```

---

生成时间：2025-12-15
