---
title: "E5 Nexus Lab — HPC"
layout: gridlay
excerpt: "E5 Nexus Lab — HPC"
sitemap: false
permalink: /hpc.html
---

- <font color='red'><b>Note that we are currently using only the Pi cluster. We may expand to other clusters at some point.</b></font>
- [交我算子账号申请](https://docs.hpc.sjtu.edu.cn/quickstart/index.html#id7)
- 使用VS Code直连登录节点可能触发"Violation of usage policy"，建议在本地使用VS Code编辑脚本后，先上传至登录节点（可通过scp、sftp、rsync、git等工具；[注意服务器端的git需配置代理](https://docs.hpc.sjtu.edu.cn/transport/faq.html)），再提交作业至计算节点。在本地使用VS Code编辑的一大优势是可以自行配置Copilot等现代AI工具，从而大幅提升编码效率。
- 如确有需要在集群上分析large datasets（不方便下载到本地），[可以申请一个计算节点](https://docs.hpc.sjtu.edu.cn/job/slurm.html#srun-salloc)，并使用VS Code的Remote-SSH插件连接该计算节点进行分析，相关`.ssh/config`配置参考如下，注意替换`$USER`、[设置免密登录](https://docs.hpc.sjtu.edu.cn/accounts/security.html#require-certificate)、以及首次连接新主机时在提示处键入yes。
  ```bash
  # ==========SJTU login and data transfer nodes==========
  Host pilogin sylogin data sydata
      HostName %h.hpc.sjtu.edu.cn
      User $USER
      IdentityFile ~/.ssh/id_rsa
      CertificateFile ~/.ssh/id_rsa-cert.pub

  # ==========SJTU compute nodes (dynamic)==========
  Host compute
      HostName casXXX
      User $USER
      IdentityFile ~/.ssh/id_rsa
      CertificateFile ~/.ssh/id_rsa-cert.pub
      ProxyJump pilogin
  ```
  ![]({{ site.url }}{{ site.baseurl }}/images/teampic/salloc-vs-code.png){: style="width: 100%; float: center; margin: 10px"}
