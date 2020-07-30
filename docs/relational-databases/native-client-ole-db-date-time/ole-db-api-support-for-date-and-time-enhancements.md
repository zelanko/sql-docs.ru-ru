---
title: Поддержка API для усовершенствований даты и времени (поставщик собственного клиента OLE DB)
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f4bb55ae2187b1406281572157457a49bda97752
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247973"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements-native-client-ole-db-provider"></a>Поддержка OLE DB API для усовершенствований даты и времени (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Следующие API-интерфейсы OLE DB поддерживают улучшенные возможности по работе с данными в формате даты-времени.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Чтобы позволить приложениям различать значения **datetime**, **datetime2** и **smalldatetime**, в структуру DBBINDING добавлен новый флаг. Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Дополнительные сведения см. в статье [инструкции по расширенному копированию для улучшенных типов даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Дополнительные сведения см. в статье [Метаданные — параметры и наборы строк](../../relational-databases/native-client-ole-db-date-time/metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Подробности о затронутых наборах строк схемы см. в статье [Метаданные — наборы строк даты и времени и схемы](../../relational-databases/native-client-ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md).|  
|IRowsetFastLoad|Данный интерфейс поддерживает новые типы даты-времени, но он остается неизменным.|  
|ITableDefinition::CreateTable|Подробнее см. статью [Улучшения поддержки типов данных даты и времени OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>См. также  
 [Улучшения функций даты и времени &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
