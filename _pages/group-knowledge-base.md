---
title: "E5 Nexus Lab — Group"
layout: gridlay
excerpt: "E5 Nexus Lab — Group"
sitemap: false
permalink: /group-knowledge-base/
---

The Group Knowledge Base provides information on getting started with local resources at the E5 Nexus Lab at SJTU. We hope that new group members will find this information helpful.

- HPC @ SJTU
  - [交我算子账号申请](https://docs.hpc.sjtu.edu.cn/quickstart/index.html#id7)
  - 使用VS Code直连登录节点可能触发"Violation of usage policy"，如下图所示。建议在本地使用VS Code编辑脚本后，先上传至登录节点（可通过scp、sftp、rsync、git等工具；[注意服务器端的git需配置代理](https://docs.hpc.sjtu.edu.cn/transport/faq.html)），再提交作业至计算节点。在本地使用VS Code编辑的一大优势是可以自行配置Copilot等现代AI工具，从而大幅提升编码效率。
    ![]({{ site.url }}{{ site.baseurl }}/images/respic/violation-of-usage-policy.png){: style="width: 100%; float: center; margin: 10px"}
  - 如确有需要在集群上分析large datasets（不方便下载到本地），[可以申请一个计算节点](https://docs.hpc.sjtu.edu.cn/job/slurm.html#srun-salloc)，并使用VS Code的Remote-SSH插件连接该计算节点进行分析，相关`.ssh/config`配置参考如下，[注意需要设置免密登录](https://docs.hpc.sjtu.edu.cn/accounts/security.html#require-certificate)、以及首次连接新主机时在提示处键入yes。
    ```bash
    # ==========SJTU login and data transfer nodes==========
    Host pilogin sylogin data sydata
        HostName %h.hpc.sjtu.edu.cn
        User test
        IdentityFile ~/.ssh/id_rsa
        CertificateFile ~/.ssh/id_rsa-cert.pub

    # ==========SJTU compute nodes (dynamic)==========
    Host compute
        HostName casXXX
        User test
        IdentityFile ~/.ssh/id_rsa
        CertificateFile ~/.ssh/id_rsa-cert.pub
        ProxyJump pilogin
    ```
    ![]({{ site.url }}{{ site.baseurl }}/images/respic/salloc-vs-code.png){: style="width: 100%; float: center; margin: 10px"}
- GEOS-Chem
  - GEOS-Chem全球大气化学传输模型的驱动数据存放在Pi集群：`/lustre/home/acct-fei.yao/share/ExtData`，如需下载更多数据，须经课题组讨论通过，如数据也会被课题组其他成员使用。自定义数据请在`HEMCO_Config.rc`中单独定义路径。
