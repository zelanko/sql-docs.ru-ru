---
title: Улучшения даты и времени (OLE DB) | Документация Майкрософт
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
ms.openlocfilehash: c4a93078b84cf5146f94043496bea0fdaed9fc80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015702"
---
# <a name="date-and-time-improvements-ole-db"></a>Улучшения функций даты и времени (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] добавлены новые типы данных даты-времени. В этом разделе описаны способы предоставления новых типов в виде расширений в драйвере OLE DB для SQL Server. Общие сведения о драйвере OLE DB для SQL Server поддержки новых типов данных даты и времени см. в разделе [улучшения даты и времени](../../oledb/features/date-and-time-improvements.md). Пример см. в разделе [Использование расширенных функций &#40;даты и времени&#41;OLE DB](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Дополнительные общие сведения о типах данных даты и времени см. в [разделе &#40;DateTime Transact-&#41;SQL](../../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Улучшения поддержки типов данных даты и времени OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Содержит сведения о типах OLE DB (Драйвер OLE DB для SQL Server), поддерживающих [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы данных даты и времени.  
  
 [OLE DB &#40;метаданных&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 Содержит сведения о структуре DBBINDING, **ICommandWithParameters:: GetParameterInfo**, **ICommandWithParameters:: SetParameterInfo**, **IColumnsRowset:: жетколумнсровсет**и I**колумнсинфо:: GetColumnInfo** . Также предоставляет сведения об обновлениях наборов строк схем OLE DB.  
  
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
  
  
