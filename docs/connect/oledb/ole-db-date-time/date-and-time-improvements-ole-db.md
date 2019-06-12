---
title: Дата и время усовершенствования (OLE DB) | Документация Майкрософт
description: Улучшения функций даты и времени (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 5518461fade08e6f23e1594056c284865957274c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66769340"
---
# <a name="date-and-time-improvements-ole-db"></a>Улучшения функций даты и времени (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] добавлены новые типы данных даты-времени. В этом разделе описывается, каким образом эти новые типы доступны в виде расширений в драйвере OLE DB для SQL Server. Обзор драйвера OLE DB для SQL Server поддержку новых типов даты и времени данных, см. в разделе [время улучшения функций даты и](../../oledb/features/date-and-time-improvements.md). Пример, см. в разделе [использования улучшенных возможностей даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Более общие сведения о типах данных даты и времени см. в разделе [datetime &#40;Transact-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Улучшения поддержки типов данных даты и времени OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Предоставляет сведения о OLE DB (драйвер OLE DB для SQL Server), типах, поддерживающих [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных даты и времени.  
  
 [Метаданные &#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 Содержит сведения о структуре DBBINDING **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset:: GetColumnsRowset**и я**ColumnsInfo::GetColumnInfo**. Также предоставляет сведения об обновлениях наборов строк схем OLE DB.  
  
 [Привязки и преобразования &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 Описывает правила преобразования существующих и новых типов данных между сервером и клиентом.  
  
 [Изменения массового копирования для расширенных типов даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Новые возможности поддержки API OLE DB для функций даты и времени](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Описывает API-интерфейсы OLE DB, поддерживающие расширенные возможности типов даты-времени.  
  
 [Сравнимость для IRowsetFind](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 Описывает типы даты и времени и **IRowsetFind**.  
 
  
## <a name="see-also"></a>См. также:  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
