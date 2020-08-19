---
description: sp_help_spatial_geometry_histogram (Transact-SQL)
title: sp_help_spatial_geometry_histogram (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_histogram
- sp_help_spatial_geometry_histogram_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_histogram
ms.assetid: 036aaf61-df3e-40f7-aa4e-62983c5a37bd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6d6e17d2e4ae048c563a2130918d137d5c186b60
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447043"
---
# <a name="sp_help_spatial_geometry_histogram-transact-sql"></a>sp_help_spatial_geometry_histogram (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Упрощает задание значений параметров ограничивающего прямоугольника и сетки для пространственного индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geometry_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @xmin = ] 'minx' ]   
     [ , [ @ymin = ] 'miny' ]   
     [ ,.[ @xmax = ] 'maxx' ]  
     [ , [ @ymax = ] 'maxy' ]  
     [ , [ @sample = ] 'sample' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @tabname = ] 'tabname'` Полное или неполное имя таблицы, для которой был указан пространственный индекс.  
  
 Кавычки требуются, только если определяется уточненная таблица. Если предоставлено полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. *табнаме* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @colname = ] 'colname'` Имя указанного пространственного столбца. *colname* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @resolution = ] 'resolution'` Разрешение ограничивающего прямоугольника. Допустимые значения: от 10 до 5000. метод *Resolution* имеет тип **tinyint**и не имеет значения по умолчанию.  
  
`[ @xmin = ] 'xmin'` Является свойством ограничивающего прямоугольника по оси X. *xmin* имеет тип **float**и не имеет значения по умолчанию.  
  
`[ @ymin = ] 'ymin'` Свойство ограничивающего прямоугольника по оси Y. *ymin* имеет тип **float**и не имеет значения по умолчанию.  
  
`[ @xmax = ] 'xmax'` Является свойством ограничивающего прямоугольника по оси X. *xmax* имеет тип **float**и не имеет значения по умолчанию.  
  
`[ @ymax = ] 'ymax'` Свойство ограничивающего прямоугольника по оси Y. *ymax* имеет тип **float**и не имеет значения по умолчанию.  
  
`[ @sample = ] 'sample'` Процент используемой таблицы. Допустимые значения: от 0 до 100. *Пример* — это **float**. По умолчанию установлено значение 100.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Возвращает табличное значение. В следующей сетке описывается содержимое столбцов таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Представляет собой уникальный идентификатор каждой ячейки, перечисление начинается с 1.|  
|**ячейку**|**geometry**|Прямоугольный многоугольник, представляющий каждую ячейку. Форма ячеек идентична форме ячеек, используемой при пространственном индексировании.|  
|**row_count**|**bigint**|Указывает количество пространственных объектов, которые ограничивают или содержат ячейку.|  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом роли **Public** . Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Комментарии  
 В пространственной таблице среды SSMS отображается графическое представление результатов. Можно повторно отправить запрос результатов с использованием пространственного окна для определения приблизительного количества элементов результатов. Объекты в таблице могут занимать более одной ячейки, поэтому сумма количества ячеек может быть больше числа фактических объектов.  
  
 В результирующий набор, в котором указано число объектов, находящихся за пределами ограничивающего прямоугольника или касающихся его, можно добавить дополнительную строку. **Целлид** этой строки равно 0, а **Ячейка** этой строки содержит **LineString** , представляющий ограничивающий прямоугольник. Эта строка представляет все пространство за пределами ограничивающего прямоугольника.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается образец таблицы, а затем вызывается **sp_help_spatial_geometry_histogram** для таблицы.  
  
 `USE AdventureWorksDW2012`  
  
 `GO`  
  
 `-- Set database compatibility for circular arc segments`  
  
 `ALTER DATABASE AdventureWorksDW2012`  
  
 `SET COMPATIBILITY_LEVEL = 110;`  
  
 `GO`  
  
 `-- Create table to execute sp_help_spatial_geometry_histogram on`  
  
 `CREATE TABLE TownSites`  
  
 `(`  
  
 `Location geometry NULL,`  
  
 `SiteName nvarchar(50) NULL`  
  
 `)`  
  
 `GO`  
  
 `-- Insert site data into table`  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('POINT(0 0)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Booth Map';`  
  
 `SET @g = geometry::Parse('POLYGON((1 1, 1 2, 2 2, 2 1, 1 1))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Town Hall';`  
  
 `SET @g = geometry::Parse('CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-1 0, 0 -1, 1 0),(1 0, 1 2, -1 0)))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Park';`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(1 5, 2 2, 5 1)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Road';`  
  
 `-- Call proc to see data within bounding box`  
  
 `EXEC sp_help_spatial_geometry_histogram @tabname = TownSites, @colname = Location, @resolution = 64, @xmin = -2, @ymin = -2, @xmax = 3, @ymax = 3, @sample = 100;`  
  
 `GO`  
  
 `DROP TABLE TownSites;`  
  
 `GO`  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры пространственного индекса &#40;языке Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
