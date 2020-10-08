---
description: sp_help_spatial_geography_histogram (Transact-SQL)
title: sp_help_spatial_geography_histogram (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_histogram_TSQL
- sp_help_spatial_geography_histogram
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_histogram
ms.assetid: 5c5bd319-055d-4cd6-8c5a-06354cc056cc
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0c7368b8991fe442cab30b724532e8899502e18f
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809396"
---
# <a name="sp_help_spatial_geography_histogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Упрощает задание значений параметров сетки для пространственного индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @tabname = ] 'tabname'` Полное или неполное имя таблицы, для которой был указан пространственный индекс.  
  
 Кавычки требуются, только если определяется уточненная таблица. Если предоставлено полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. *табнаме* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @colname = ] 'columnname'` Имя указанного пространственного столбца. *ColumnName* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @resolution = ] 'resolution'` Разрешение ограничивающего прямоугольника. Допустимые значения: от 10 до 5000. метод *Resolution* имеет тип **tinyint**и не имеет значения по умолчанию.  
  
`[ @sample = ] 'sample'` Процент используемой таблицы. Допустимые значения: от 0 до 100. *TABLESAMPLE* — это **float**. По умолчанию установлено значение 100.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Возвращает табличное значение. В следующей сетке описывается содержимое столбцов таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Представляет собой уникальный идентификатор каждой ячейки, отсчет начинается с 1.|  
|**ячейку**|**geography**|Прямоугольный многоугольник, представляющий каждую ячейку. Форма ячеек идентична форме ячеек, используемой при пространственном индексировании.|  
|**row_count**|**bigint**|Указывает количество пространственных объектов, которые ограничивают или содержат ячейку.|  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом роли **Public** . Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Комментарии  
 В пространственной таблице среды SSMS отображается графическое представление результатов. Можно повторно отправить запрос результатов с использованием пространственного окна для определения приблизительного количества элементов результатов.  
  
> [!NOTE]  
>  Объекты в таблице могут занимать более одной ячейки, поэтому сумма количества ячеек в таблице может быть больше числа фактических объектов.  
  
 Ограничивающим прямоугольником для типа **Geography** является весь глобус.  
  
## <a name="examples"></a>Примеры  
 В следующем примере вызывается  **sp_help_spatial_geography_histogram** для `Person.Address` таблицы в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базе данных.  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры пространственного индекса &#40;языке Transact-SQL&#41;](./spatial-index-stored-procedures-arguments-and-properties.md)  
  
