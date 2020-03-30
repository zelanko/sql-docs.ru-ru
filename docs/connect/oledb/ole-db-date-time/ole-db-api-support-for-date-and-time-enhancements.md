---
title: Новые возможности поддержки API OLE DB для функций даты и времени | Документы Майкрософт
description: Новые возможности поддержки API OLE DB для функций даты и времени
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c2671b3df6432e63c0e0b36a24bade60286f72a7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015681"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Новые возможности поддержки API OLE DB для функций даты и времени
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Следующие API-интерфейсы OLE DB поддерживают улучшенные возможности по работе с данными в формате даты-времени.  
  
|Компонент|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Чтобы позволить приложениям различать значения **datetime**, **datetime2** и **smalldatetime**, в структуру DBBINDING добавлен новый флаг. Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Подробнее см. статью [Изменения массового копирования для расширенных типов даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md).|  
|ICommandWithParameters::GetParameterInfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Подробности о затронутых наборах строк схемы см. в статье [Метаданные — наборы строк даты и времени и схемы](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Данный интерфейс поддерживает новые типы даты-времени, но он остается неизменным.|  
|ITableDefinition::CreateTable|Подробнее см. статью [Улучшения поддержки типов данных даты и времени OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>См. также:  
 [Улучшения функций даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
