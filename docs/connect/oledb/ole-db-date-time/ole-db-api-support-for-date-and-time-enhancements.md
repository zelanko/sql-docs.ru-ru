---
title: Поддержка API-Интерфейс OLE DB для даты и времени улучшения | Документы Microsoft
description: Поддержка OLE DB API для усовершенствованиями даты и времени
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b614acdd644369ae3cf04f88edac5a88163e767
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Поддержка API-Интерфейс OLE DB для даты и времени усовершенствования
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Следующие API-интерфейсы OLE DB поддерживают улучшенные возможности по работе с данными в формате даты-времени.  
  
|Функция|Описание|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Чтобы позволить приложениям различать структуры DBBINDING добавляется флаг **datetime**, **datetime2**, и **smalldatetime** значения. Дополнительные сведения см. в разделе [строк метаданные параметров и](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Дополнительные сведения см. в разделе [изменения массового копирования для улучшенной даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md).|  
|ICommandWithParameters::GetParameterInfo|Дополнительные сведения см. в разделе[строк метаданные параметров и](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Дополнительные сведения см. в разделе[строк метаданные параметров и](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Дополнительные сведения см. в разделе[строк метаданные параметров и](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Дополнительные сведения см. в разделе[строк метаданные параметров и](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Сведения о затронутых наборах строк схемы см. в разделе[даты и времени и наборы строк схемы](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Данный интерфейс поддерживает новые типы даты-времени, но он остается неизменным.|  
|ITableDefinition::CreateTable|Дополнительные сведения см. в разделе [поддержка типов данных даты OLE DB и улучшения времени](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>См. также  
 [Дата и время усовершенствования & #40; OLE DB & #41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
