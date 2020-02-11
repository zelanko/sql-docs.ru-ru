---
title: Новые возможности поддержки API OLE DB для функций даты и времени | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef6334f6fe4671f2563add857f6dd58ce67a2840
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63237846"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Новые возможности поддержки API OLE DB для функций даты и времени
  Следующие API-интерфейсы OLE DB поддерживают улучшенные возможности по работе с данными в формате даты-времени.  
  
|Компонент|Description|  
|--------------|-----------------|  
|IAccessor:: CreateAccessor|Чтобы позволить приложениям различать значения `datetime`, `datetime2` и `smalldatetime`, в структуру DBBINDING добавляется флаг. Дополнительные сведения см. в разделе [метаданные параметров и наборов строк](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Дополнительные сведения см. в статье [инструкции по расширенному копированию для улучшенных типов даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Дополнительные сведения см. в разделе[метаданные параметров и наборов строк](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Дополнительные сведения см. в разделе[метаданные параметров и наборов строк](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Дополнительные сведения см. в разделе[метаданные параметров и наборов строк](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Дополнительные сведения см. в разделе[метаданные параметров и наборов строк](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset:: Rowset|Дополнительные сведения о затронутых наборах строк схемы см. в разделе[Дата и время и наборы строк схемы](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Данный интерфейс поддерживает новые типы даты-времени, но он остается неизменным.|  
|ITableDefinition::CreateTable|Дополнительные сведения см. в разделе [Поддержка типов данных для OLE DB улучшения даты и времени](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>См. также:  
 [Улучшения даты и времени &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
