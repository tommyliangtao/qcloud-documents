## 功能简介
将节点收到的用户请求 URL，按照指定规则，在节点向源站发起请求时重写到源站上的目标 URL，不影响节点的缓存标识（Cache Key）。

## 适用场景
若客户端访问的 URL 已经对外发布，不宜更改，而业务源站出于某些原因变更了源站上的 URL 路径；或者为了搜索引擎优化（SEO），客户端访问的 URL 和源站 URL 的路径并不一致。在这些情况下，通过设置回源 URL 重写规则，节点可以在不改变客户端访问 URL 的情况下，把回源的 URL 重写为源站上资源对应的实际 URL。

## 操作步骤
1. 登录 [边缘安全加速平台控制台](https://console.cloud.tencent.com/edgeone)，在左侧菜单栏中，单击**规则引擎**。
2. 在规则引擎页面，选择所需站点，可按需配置访问 URL 重定向规则。如何使用规则引擎，请参见 [规则引擎](https://cloud.tencent.com/document/product/1552/70901)。
   配置项说明：
<table>
<thead>
<tr>
<th width="20%">配置项</th>
<th width="80%">说明</th>
</tr>
</thead>
<tbody><tr>
<td align="left">类型</td>
<td align="left">重写类型：<ul><li>增加路径前缀：增加指定路径前缀至请求 URL Path，例如请求 URL是 <code>http://www.example.com/path0/index.html</code>,增加的路径前缀为/prefix，则重写后的 URL 是 <code>http://www.example.com/prefix/path0/index.html</code></li><li> 移除路径前缀：移除请求 URL 的指定路径前缀内，例如请求 URL是 <code>http://www.example.com/path0/path1/index.html</code>，指定移除的路径前缀是/path0，则重写后的 URL 是 <code>http://www.example.com/path1/index.html</code></li><li>替换完整路径：替换完整的请求 URL Path，例如请求 URL是 <code>http://www.example.com/path0/index.html</code>，替换完整路径为/new/page.html，则重写后的 URL 是 <code>http://www.example.com/new/page.html</code></li></ul></td>
</tr>
<tr>
<td align="left">携带查询参数</td>
<td align="left">是否携带原查询参数至目标 URL ，默认会携带</td>
</tr>
</tbody></table>

## 配置示例

若请求 URL `https://www.example.com/path0/path1/foo.html` 的访问 URL 重定向配置如下：

![](https://qcloudimg.tencent-cloud.cn/raw/8e5a2b2af622f99d7454c2e85c8fbfaf.png)

则客户端请求：`https://www.example.com/path0/path1/foo.html?key1=value1` 回源会被重写为 `https://www.example.com/path1/foo.html` 获取请求资源。
