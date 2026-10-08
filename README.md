# gsc-wp — GSC + WP + SEO（MCP 工具集）

[![Listed on mcpservers.org](https://mcpservers.org/badge.svg)](https://mcpservers.org/servers/wjjnew123/gsc-wp)

Google Search Console 搜索数据 + WordPress 内容读取 + SEO 机会分析，共 **22 个只读工具**。

- 聚合端点：`https://mcpweb.wjjnew.cn/gsc-wp/mcp`
- 拆分端点：`/gsc/mcp`（GSC 8）、`/wp/mcp`（WordPress 11）、`/seo/mcp`（SEO 3）
- 鉴权：`Authorization: Bearer mcp_sk_xxx`
- 控制台 / 文档：https://mcpweb.wjjnew.cn/ · https://mcpweb.wjjnew.cn/gsc-wp-guide.html

## 使用前：配置数据源（隐私保护）

到 https://mcpweb.wjjnew.cn/ 控制台「**数据源**」配置你自己的凭据（AES-256-GCM 加密存储，仅你本人可用）：
- **Google Search Console**：服务账号 JSON + 站点属性（`sc-domain:example.com` 或 `https://example.com/`）。
- **WordPress**：站点地址 + 用户名 + 应用密码（建议只读）；如需商品完整字段，填 WooCommerce Consumer Key/Secret。
- **SEO** 工具需**同时**配置 GSC 与 WordPress。

## 客户端配置

```json
{
  "mcpServers": {
    "gsc-wp": {
      "type": "http",
      "url": "https://mcpweb.wjjnew.cn/gsc-wp/mcp",
      "headers": { "Authorization": "Bearer <你的 mcp_sk_xxx>" }
    }
  }
}
```

## 工具清单（22）

- **GSC（8）**：`gsc_list_sites` `gsc_search_analytics` `gsc_top_queries` `gsc_page_performance` `gsc_query_page_pairs` `gsc_compare_periods` `gsc_url_inspection` `gsc_list_sitemaps`
- **WordPress（11）**：`wp_get_posts` `wp_get_pages` `wp_get_post_by_url` `wp_get_post` `wp_search` `wp_get_categories` `wp_get_tags` `wp_get_media` `wp_get_site_info` `wp_get_cpt` `wp_get_woo_products`
- **SEO（3）**：`seo_find_opportunities` `seo_audit_url` `seo_ctr_benchmark`

全部只读；开启写入后 WordPress 另有写入工具（默认关闭）。

## 本地部署（可选）

源码运行（自备站点与密钥），见 `.env.example`；客户端 stdio 各工具分别配置 `GSC_KEY_FILE`/`GSC_SITE_URL`、`WP_SITE_URL`/`WP_USERNAME`/`WP_APP_PASSWORD`。

## 许可

MIT（见 [LICENSE](./LICENSE)）。仅用于自有/授权站点与数据。
