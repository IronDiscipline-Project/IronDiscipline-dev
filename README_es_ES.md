[🇺🇸 English](README_en_US.md) | [🇩🇪 Deutsch](README_de_DE.md) | [🇪🇸 Español](README_es_ES.md) | [🇨🇳 中文](README_zh_CN.md) | [🇯🇵 日本語](README_ja_JP.md)

# IronDiscipline-dev (Disciplina de Hierro - Edición Folia)

Plugin integral de gestión y disciplina para servidores de Minecraft.
Diseñado para servidores de RP militar y de prisiones.

> ⚡ **¡Esta versión es exclusiva para Folia!** Los datos de rango se almacenan en una base de datos dedicada. LuckPerms no es necesario.
> Para PaperSpigot, utilice [IronDiscipline](https://github.com/IronDiscipline-Project/IronDiscipline).

## Diferencias con la Versión Estándar

| Elemento | Estándar (IronDiscipline) | Dev (IronDiscipline-dev) |
|---|---|---|
| Servidor | PaperSpigot 1.18+ | Folia 1.18+ |
| Almacenamiento de Rangos | Metadatos de LuckPerms | BD propia (H2/MySQL) |
| LuckPerms | Requerido | No requerido (opcional para migración) |
| Rendimiento | Vía API | BD directa + Caché |
| Concurrencia | Estándar | Procesamiento concurrente seguro de hilos |
| Soporte de Folia | No compatible | Totalmente compatible (exclusivo) |

## Características

- **Sistema de Rangos**: Gestión de permisos por rango
  - Caché concurrente seguro de hilos (`ConcurrentHashMap`)
  - Protección contra condiciones de carrera
- **PTS (Permiso para Hablar)**: Sistema de permiso de habla
- **Integración con Discord**: Vinculación de cuentas, sincronización de roles
- **Sistema de Advertencias**: Advertencias con castigo automático
  - Prevención de encarcelamientos duplicados
  - Copia de seguridad instantánea del inventario para evitar pérdida de objetos
  - Detección y reparación automática de inconsistencias de datos
- **Sistema de Exámenes**: Exámenes de promoción con GUI
- **Migración de Datos**: Migración fácil desde LuckPerms con `/irondev migrate`
- **Folia Exclusivo**: Programación nativa de Folia a través de MorePaperLib

## Requisitos

- Java 17+
- Folia 1.18+ (**PaperSpigot no compatible**)
- MySQL, SQLite o H2 Database (predeterminado)

## Instalación

1. Descargar el JAR más reciente de [Releases](https://github.com/IronDiscipline-Project/IronDiscipline-dev/releases)
2. Colocar en la carpeta `plugins` del servidor
3. Iniciar el servidor
4. Editar `plugins/IronDisciplineDev/config.yml` según sea necesario

## Migración desde Versión Estándar

```
/irondev migrate
```

## Comandos

### 🔧 Comandos de Versión Dev
| Comando | Descripción | Permiso |
|---|---|---|
| `/irondev migrate` | Migrar datos desde LuckPerms | `iron.admin` |
| `/irondev status` | Mostrar estado | `iron.admin` |
| `/iron addon install <id\|owner/repo\|URL>` | Instalar un addon | `iron.admin` |
| `/iron addon list` | Listar addons instalados | `iron.admin` |
| `/iron addon certified` | Listar addons certificados | `iron.admin` |
| `/iron addon remove <id>` | Desinstalar un addon | `iron.admin` |
| `/iron addon refresh` | Actualizar registro de addons | `iron.admin` |

## Add-ons

IronDiscipline-dev incluye un gestor de addons integrado mediante `/iron addon`.

### Instalación (3 métodos)

```
# 1. Addon certificado (revisado por el equipo IrDi)
/iron addon install <id>

# 2. Directamente desde un GitHub Release
/iron addon install <owner/repo>

# 3. URL directa (solo HTTPS, límite 50 MB)
/iron addon install https://example.com/myaddon.jar
```

Usa `/iron addon certified` para ver el registro oficial de addons.

Documentación para desarrolladores: [docs/ADDON_DEVELOPMENT.md](docs/ADDON_DEVELOPMENT.md).

## Compilar

```bash
mvn clean package
```

## Licencia

MIT License
