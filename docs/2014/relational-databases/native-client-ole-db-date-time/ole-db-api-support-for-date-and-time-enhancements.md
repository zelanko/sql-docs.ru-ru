---
title: Поддержка API-Интерфейс OLE DB для даты и времени улучшения | Документы Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bf7eee4dd2517d4ff9c9f871160ba0515b18ce8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194920"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Поддержка API-Интерфейс OLE DB для даты и времени усовершенствования
  Следующие API-интерфейсы OLE DB поддерживают улучшенные возможности по работе с данными в формате даты-времени.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Чтобы позволить приложениям различать значения `datetime`, `datetime2` и `smalldatetime`, в структуру DBBINDING добавляется флаг. Дополнительные сведения см. в разделе [строк метаданные параметров и](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Дополнительные сведения см. в разделе [изменения массового копирования для улучшенной даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Дополнительные сведения см. в разделе[строк метаданные параметров и](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Дополнительные сведения см. в разделе[строк метаданные параметров и](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Дополнительные сведения см. в разделе[строк метаданные параметров и](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Дополнительные сведения см. в разделе[строк метаданные параметров и](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Сведения о затронутых наборах строк схемы см. в разделе[даты и времени и наборы строк схемы](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Данный интерфейс поддерживает новые типы даты-времени, но он остается неизменным.|  
|ITableDefinition::CreateTable|Дополнительные сведения см. в разделе [поддержка типов данных даты OLE DB и улучшения времени](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>См. также  
 [Дата и время улучшениях &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  