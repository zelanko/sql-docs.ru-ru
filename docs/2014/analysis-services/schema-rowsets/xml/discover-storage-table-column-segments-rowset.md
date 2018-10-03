---
title: Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 111aa44a99c59fdc4bb9953903e2827c79b54104
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133489"
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS
  Содержит сведения на уровне столбцов и сегментов о таблицах хранилища, используемых в базе данных служб Analysis Services, работающей в табличном режиме или режиме PowerPivot. Этот набор строк используется главным образом для анализа и устранения неполадок.  
  
 **Применимо к:** табличные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` Набор строк содержит следующие столбцы.  
  
|**Имя столбца**|**Индикатор типа**|**Ограничение**|**Описание**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Да|Указывает табличную базу данных.<br /><br /> `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` Набора строк можно ограничить с помощью этого столбца. Если отсутствует, используется текущая база данных.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Да|Имя модели.<br /><br /> `DISCOVER_STORAGE_TABLES` Набора строк можно ограничить с помощью этого столбца.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Да|Имя группы мер.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Да|Имя секции.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Имя измерения.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Внутренний идентификатор сегмента таблицы.|  
|`COLUMN_ID`|`DBTYPE_WSTR`||Внутренний идентификатор столбца.|  
|`SEGMENT _NUMBER`|`DBTYPE_I8`||Порядковый номер сегмента в таблице.|  
|`TABLE_PARTTION_NUMBER`|`DBTYPE_I8`||Порядковый номер секции.|  
|`RECORDS_COUNT`|`DBTYPE_I8`||Количество записей в секции.|  
|`ALLOCATED_SIZE`|`DBTYPE_UI8`||Размер в байтах, выделенный сегменту столбцов.|  
|`USED_SIZE`|`DBTYPE_UI8`||Размер в байтах, используемый сегментом столбцов.|  
|`COMPRESSION_TYPE`|`DBTYPE_WSTR`||Тип сжатия, примененный к сегменту столбца. Это значение предназначено только для внутреннего использования и поддержки пользователей. Корпорация Майкрософт не публикует действительные значения или описания для этого столбца.|  
|`BITS_COUNT`|`DBTYPE_I8`||Число битов.|  
|`BOOKMARK_BITS_COUNT`|`DBTYPE_I8`||Число битов закладки.|  
|`VERTIPAQ_STATE`|`DBTYPE_WSTR`||Состояние сжатия VertiPaq для этого сегмента столбца. Значение может быть одним из следующих:<br /><br /> -SKIPPED — сжатие VertiPaq пропущено.<br />-ВЫПОЛНИТЬ — сжатие VertiPaq выполнено успешно.<br />Сжатие - ВЫЧИСЛЕНО – VertiPaq было вычислено.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a>Пример  
 Следующий запрос возвращает сегменты таблицы хранилища, связанные с атрибутом модели LastName, в текущей базе данных.  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы служб Analysis Services](../analysis-services-schema-rowsets.md)  
  
  
