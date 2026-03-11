[🇺🇸 English](README_en_US.md) | [🇩🇪 Deutsch](README_de_DE.md) | [🇪🇸 Español](README_es_ES.md) | [🇨🇳 中文](README_zh_CN.md) | [🇯🇵 日本語](README_ja_JP.md)

# IronDiscipline-dev (铁纪律 - Folia专用版)

Minecraft服务器综合管理与纪律插件。
专为军事和监狱RP服务器设计。

> ⚡ **此版本为Folia专用！** 军衔数据存储在独立数据库中，不依赖LuckPerms。
> 如需使用PaperSpigot，请使用 [IronDiscipline](https://github.com/IronDiscipline-Project/IronDiscipline)。

## 与标准版的区别

| 项目 | 标准版 (IronDiscipline) | Dev版 (IronDiscipline-dev) |
|---|---|---|
| 服务器 | PaperSpigot 1.18+ | Folia 1.18+ |
| 军衔存储 | LuckPerms元数据 | 独立数据库 (H2/MySQL) |
| LuckPerms | 必需 | 不需要（仅迁移时可选） |
| 性能 | 通过API | 直接数据库+缓存 |
| 并发处理 | 标准 | 线程安全并发处理 |
| Folia支持 | 不支持 | 完全支持（专用） |

## 功能

- **军衔系统**：按军衔管理权限
  - 线程安全并发缓存（`ConcurrentHashMap`）
  - 竞态条件防护
- **PTS（发言许可）**：下级发言许可系统
- **Discord集成**：账号关联、角色同步
- **警告系统**：警告累积自动处罚
  - 防止重复监禁
  - 即时背包备份防止物品丢失
  - 自动检测和修复数据不一致
- **考试系统**：GUI晋升考试
- **数据迁移**：使用 `/irondev migrate` 从LuckPerms轻松迁移
- **Folia专用**：通过MorePaperLib实现Folia原生调度

## 要求

- Java 17+
- Folia 1.18+（**不支持PaperSpigot**）
- MySQL、SQLite 或 H2 Database（默认）

## 安装

1. 从 [Releases](https://github.com/IronDiscipline-Project/IronDiscipline-dev/releases) 下载最新JAR
2. 放入服务器的 `plugins` 文件夹
3. 启动服务器
4. 根据需要编辑 `plugins/IronDisciplineDev/config.yml`

## 从标准版迁移

```
/irondev migrate
```

## 命令

### 🔧 Dev版命令
| 命令 | 描述 | 权限 |
|---|---|---|
| `/irondev migrate` | 从LuckPerms迁移数据 | `iron.admin` |
| `/irondev status` | 显示状态 | `iron.admin` |
| `/iron addon install <id\|owner/repo\|URL>` | 安装插件扩展 | `iron.admin` |
| `/iron addon list` | 列出已安装的扩展 | `iron.admin` |
| `/iron addon certified` | 列出认证扩展 | `iron.admin` |
| `/iron addon remove <id>` | 卸载扩展 | `iron.admin` |
| `/iron addon refresh` | 强制刷新认证注册表 | `iron.admin` |

## 插件扩展（Addon）

IronDiscipline-dev 内置了通过 `/iron addon` 命令管理扩展的功能。

### 安装方式（3种）

```
# 1. 认证扩展（经 IrDi 团队审核）
/iron addon install <id>

# 2. 从 GitHub Release 直接获取
/iron addon install <owner/repo>

# 3. 直接指定 URL（仅 HTTPS，限制 50 MB）
/iron addon install https://example.com/myaddon.jar
```

使用 `/iron addon certified` 可查看官方认证扩展列表。

扩展开发文档：[docs/ADDON_DEVELOPMENT.md](docs/ADDON_DEVELOPMENT.md)。

## 构建

```bash
mvn clean package
```

## 许可证

MIT License
