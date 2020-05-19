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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ba55a2a8fe0ad873c4b5433a53972c441b535333
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704987"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Новые возможности поддержки API OLE DB для функций даты и времени
  Следующие API-интерфейсы OLE DB поддерживают улучшенные возможности по работе с данными в формате даты-времени.  
  
|Функция|Описание|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Чтобы позволить приложениям различать значения `datetime`, `datetime2` и `smalldatetime`, в структуру DBBINDING добавляется флаг. Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Дополнительные сведения см. в статье [инструкции по расширенному копированию для улучшенных типов даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Подробности о затронутых наборах строк схемы см. в статье [Метаданные — наборы строк даты и времени и схемы](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Данный интерфейс поддерживает новые типы даты-времени, но он остается неизменным.|  
|ITableDefinition::CreateTable|Подробнее см. статью [Улучшения поддержки типов данных даты и времени OLE DB](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>См. также  
 [Улучшения функций даты и времени &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
