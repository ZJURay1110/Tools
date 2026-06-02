# GIS 开发

---

## 1 分类简介

地理信息系统开发涉及空间数据的管理、可视化与分析。GIS 工具链覆盖了从桌面制图到服务发布再到前端展示的全流程。

!!! tip ""
    根据场景快速选择：
    - 桌面制图与分析 → [ArcGIS Pro](desktop/arcgis_pro.md) 或 [QGIS](desktop/qgis.md)
    - 发布 OGC 服务 → [GeoServer](server/geoserver.md)
    - 空间数据库查询 → [PostGIS](spatial_db/postgis.md)
    - 浏览器地图展示 → [Leaflet](webgis/leaflet.md) 或 [Mapbox GL JS](webgis/mapbox_gl_js.md)
    - 格式转换 / 栅格处理 → [GDAL](spatial_tool/gdal.md)
    - Python 脚本空间分析 → [GeoPandas](spatial_tool/geopandas.md)
    - 遥感影像处理 → [Google Earth Engine](rs/google_earth_engine.md) 或 [ENVI](rs/envi.md)

---

## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 编辑和符号化空间数据 | QGIS / ArcGIS 功能太复杂不知从何学起 | 桌面 GIS 提供制图模板 + 符号库 + WYSIWYG 排版 |
| 将地图发布为 Web 服务 | 不懂 OGC 标准、手动切片费时 | 服务端 GIS 自动发布 WMS/WFS/WMTS 标准服务 |
| 存储和查询空间数据 | 普通数据库不支持几何对象和空间索引 | 空间数据库原生支持 PostGIS 函数和 GiST 索引 |
| 在网页中渲染地图 | 从零实现地图渲染引擎几乎不可能 | Web GIS 框架一行代码加载瓦片地图 |
| 数据格式转换频繁 | Shapefile / GeoJSON / GPKG 格式互转繁琐 | 空间数据处理工具一行命令完成格式转换 |
| 处理卫星影像 | 影像下载、校正、分类知识门槛很高 | 遥感平台提供在线影像浏览和云端分析 |

---

## 3 子分类速览

### 3.1 桌面 GIS

空间数据编辑、制图、空间分析和地图发布的一体化桌面平台。

| 工具 | 一句话 |
|------|--------|
| ArcGIS Pro | ESRI 旗舰桌面 GIS，2D/3D 一体化制图与分析 |
| QGIS | 开源桌面 GIS 首选，插件丰富，社区活跃 |
| ArcGIS Desktop | ArcMap 经典版，GIS 老用户的习惯工具 |

> [进入桌面 GIS 分类](desktop/index.md)

### 3.2 服务端 GIS

将空间数据发布为符合 OGC 标准的网络服务（WMS / WFS / WCS / WMTS）。

| 工具 | 一句话 |
|------|--------|
| GeoServer | 开源 GIS 服务器首选，WMS/WFS/WCS 全支持 |
| ArcGIS Server | ESRI 企业级 GIS 服务器，与 ArcGIS 生态无缝协作 |
| ArcGIS Enterprise | ArcGIS Server + Portal + Data Store 全栈方案 |

> [进入服务端 GIS 分类](server/index.md)

### 3.3 空间数据库

为关系数据库添加空间数据类型、空间索引和支持标准 SQL 的空间查询函数。

| 工具 | 一句话 |
|------|--------|
| PostGIS | PostgreSQL 空间扩展，开源 GIS 后端核心 |
| SpatiaLite | SQLite 的空间扩展，轻量级单文件空间数据库 |
| Oracle Spatial | Oracle 商业数据库的空间模块，企业级存储方案 |

> [进入空间数据库分类](spatial_db/index.md)

### 3.4 Web GIS 框架

在浏览器中加载和渲染地图的前端 JavaScript 框架。

| 工具 | 一句话 |
|------|--------|
| Leaflet | 轻量移动端友好的 JS 地图库，入门首选 |
| OpenLayers | 功能最全的开源 Web GIS 框架 |
| Mapbox GL JS | 矢量瓦片 + 3D 地图的前端渲染引擎 |
| Cesium | 三维地球可视化，支持 WGS84 坐标系和地形 |
| deck.gl | Uber 出品的大规模数据可视化图层框架 |

> [进入 Web GIS 框架分类](webgis/index.md)

### 3.5 空间数据处理

命令行下的空间数据转换、投影变换和几何操作工具。

| 工具 | 一句话 |
|------|--------|
| GDAL | 栅格数据处理的标准库，支持 200+ 格式 |
| OGR2OGR | 矢量数据格式转换，Shapefile / GeoJSON / GPKG 互转 |
| GeoPandas | Python 中的空间数据框，Pandas + Shapely 组合 |
| Fiona | Python 中读写矢量文件的底层接口 |

> [进入空间数据处理分类](spatial_tool/index.md)

### 3.6 遥感

卫星和航空影像的处理、分类、分析和可视化。

| 工具 | 一句话 |
|------|--------|
| ENVI | 商业遥感软件，影像预处理和分析标准 |
| ERDAS Imagine | 历史最久的遥感处理软件之一 |
| Google Earth Engine | 云端遥感大数据平台，在线脚本分析 PB 级影像 |
| SNAP | ESA 开源的哨兵卫星数据处理工具 |

> [进入遥感分类](rs/index.md)

---

> [回到工具首页](../index.md)
