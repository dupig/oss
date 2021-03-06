# 使用Bucket Policy授权其他用户访问OSS资源 {#concept_ahc_tx4_j2b .concept}

您可以通过Bucket Policy授权其他用户访问您的OSS资源。

相比于[RAM Policy](../../../../intl.zh-CN/用户指南/授权管理/授权策略管理.md#)，Bucket Policy支持在控制台直接进行图形化配置操作，并且Bucket拥有者直接可以进行访问授权。Bucket Policy常见的应用场景如下：

-   向其他账号的RAM用户授权访问。

    您可以授予其他账号的RAM用户访问您的OSS资源的权限。

-   向匿名用户授予带特定IP条件限制的访问权限。

    某些场景下，您需要向匿名用户授予带IP限制的访问策略。例如，企业内部的机密文档，只允许在企业内部访问，不允许在其他区域访问。由于企业内部人员较多，如果针对每个人配置RAM Policy，工作量非常大。此时，您可以基于Bucket Policy设置带IP限制的访问策略，从而高效方便地进行授权。


## 向其他账号的RAM用户授权访问 {#section_nbp_by4_j2b .section}

1.  登录[OSS 管理控制台](https://oss.console.aliyun.com/)。
2.  在左侧存储空间列表中，单击需要授权的存储空间名称，打开该存储空间概览页面。
3.  单击文件管理页签，然后单击**授权**。
4.  在授权页面，单击**新增授权**。
5.  在新增授权页面，设置授权资源。
    -   整个Bucket：授权策略针对整个Bucket生效。
    -   指定资源：授权策略只针对指定的资源生效。您需要同时输入资源路径，例如：abc/myphoto.png。如果是针对目录授权，需要在目录结尾处加上星号（\*），例如：abc/\*。
6.  在授权用户区域，输入被授权用户的账号ID。如果需要授权多个用户，输入多个账号ID，用英文逗号（,）分隔。
7.  设置授权操作。
    -   只读：对相关资源仅有读权限。
    -   读/写：对相关资源有读和写权限。
    -   完全控制：对相关资源有所有操作的权限。
    -   拒绝访问：拒绝对相关资源的所有操作。

        **说明：** 若针对某用户同时配置了多个Bucket Policy规则，那么该用户所拥有的权限是所有Policy规则的叠加，但是拒绝访问优先。例如，针对某用户第一次设置了只读权限，第二次设置了读/写权限，那么该用户最终的权限为只读和读/写权限的叠加，即读/写权限。如果第三次设置了拒绝访问权限，则该用户最终的权限为拒绝访问。

8.  （可选）设置条件来限定此用户使用特定IP地址访问OSS资源，即设置IP等于或IP不等于某一IP地址或IP地址段：
    -   IP地址，例如：10.10.10.10。如有多个IP地址，用英文逗号（,）分隔。
    -   IP地址段，例如：10.10.10.1/24。
9.  单击**确定**。

## 向匿名用户授予带特定IP条件限制的访问权限 {#section_byf_gz4_j2b .section}

1.  登录[OSS 管理控制台](https://oss.console.aliyun.com/)。
2.  在左侧存储空间列表中，单击需要授权的存储空间名称，打开该存储空间概览页面。
3.  单击文件管理页签，然后单击**授权**。
4.  在授权页面，单击**新增授权**。
5.  在新增授权页面，设置授权资源。
    -   整个Bucket：授权策略针对整个Bucket生效。
    -   指定资源：授权策略只针对指定的资源生效。您需要同时输入资源路径，例如：abc/myphoto.png。如果是针对目录授权，需要在目录结尾处加上星号（\*），例如：abc/\*。
6.  在授权用户区域，勾选所有用户（\*）。

    **警告：** 授予所有用户访问权限时，强烈建议您设置IP条件限制。如果不设置IP条件限制，则任何人都可以访问该资源。

7.  设置授权操作。
    -   只读：对相关资源仅有读权限。
    -   读/写：对相关资源有读和写权限。
    -   完全控制：对相关资源有所有操作的权限。
    -   拒绝访问：拒绝对相关资源的所有操作。

        **说明：** 若针对某些用户同时配置了多个Bucket Policy规则，那么这些用户所拥有的权限是所有Policy规则的叠加，但是拒绝访问优先。例如，针对某些用户第一次设置了只读权限，第二次设置了读/写权限，那么这些用户最终的权限为只读和读/写权限的叠加，即读/写权限。如果第三次设置了拒绝访问权限，则这些用户最终的权限为拒绝访问。

8.  设置条件。您可以设置IP等于或IP不等于某一IP地址或IP地址段：
    -   IP地址，例如：10.10.10.10。如有多个IP地址，用英文逗号（,）分隔。
    -   IP地址段，例如：10.10.10.1/24。
9.  单击**确定**。

