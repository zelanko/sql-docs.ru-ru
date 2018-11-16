---
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2fa398eade8b3cac1497c1168882dbacbc6e9817
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659493"
---
# <a name="sphelpspatialgeographyhistogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Упрощает задание значений параметров сетки для пространственного индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@tabname =**] **"***tabname***"**  
 Полное или неполное имя определенной таблицы, для которой был указан пространственный индекс.  
  
 Кавычки требуются, только если определяется уточненная таблица. Если предоставлено полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. *tabname* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@colname =** ] **"***columnname***"**  
 Имя указанного пространственного столбца. *ColumnName* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@resolution =** ] **"***разрешение***"**  
 Разрешение ограничивающего прямоугольника. Допустимые значения: от 10 до 5000. *разрешение* — **tinyint**, не имеет значения по умолчанию.  
  
 [  **@sample =** ] **"***пример***"**  
 Используемая область таблицы (в процентах). Допустимые значения: от 0 до 100. *TABLESAMPLE* — **float**. По умолчанию установлено значение 100.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Возвращает табличное значение. В следующей сетке описывается содержимое столбцов таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Представляет собой уникальный идентификатор каждой ячейки, отсчет начинается с 1.|  
|**ячейки**|**geography**|Прямоугольный многоугольник, представляющий каждую ячейку. Форма ячеек идентична форме ячеек, используемой при пространственном индексировании.|  
|**row_count**|**bigint**|Указывает количество пространственных объектов, которые ограничивают или содержат ячейку.|  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом **открытый** роли. Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Примечания  
 В пространственной таблице среды SSMS отображается графическое представление результатов. Можно повторно отправить запрос результатов с использованием пространственного окна для определения приблизительного количества элементов результатов.  
  
> [!NOTE]  
>  Объекты в таблице могут занимать более одной ячейки, поэтому сумма количества ячеек в таблице может быть больше числа фактических объектов.  
  
 Ограничивающий прямоугольник для **geography** типа является вся планета.  
  
## <a name="examples"></a>Примеры  
 В следующем примере вызывается **sp_help_spatial_geography_histogram** на `Person.Address` в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных.  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры пространственного индекса &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
