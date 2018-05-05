---
title: Дата и время усовершенствования (OLE DB) | Документы Microsoft
description: Усовершенствования даты и времени (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 64de1f9be2fd802757feeba1f238f6c31f81c01d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="date-and-time-improvements-ole-db"></a>Дата и время усовершенствования (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] добавлены новые типы данных даты-времени. В этом разделе описывается, каким образом эти новые типы доступны в виде расширений в драйвер OLE DB для SQL Server. Обзор драйвер OLE DB для SQL Server поддержку новые типы даты и времени типов данных см. в разделе [даты и времени усовершенствования](../../oledb/features/date-and-time-improvements.md). Пример см. в разделе [использование улучшенных возможностей даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Дополнительные общие сведения о типах данных даты и времени см. в разделе [datetime &#40;Transact-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Улучшения поддержки типов данных даты и времени OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Предоставляет сведения о OLE DB (драйвер OLE DB для SQL Server) типы, которые поддерживают [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных даты и времени.  
  
 [Метаданные &#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 Содержит сведения о структуре DBBINDING **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset:: GetColumnsRowset**и я**ColumnsInfo::GetColumnInfo**. Также предоставляет сведения об обновлениях наборов строк схем OLE DB.  
  
 [Привязки и преобразования &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 Описывает правила преобразования существующих и новых типов данных между сервером и клиентом.  
  
 [Массовое копирование изменения для типы улучшенные даты и времени &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Новые возможности поддержки API OLE DB для функций даты и времени](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Описывает API-интерфейсы OLE DB, поддерживающие расширенные возможности типов даты-времени.  
  
 [Сравнимость для IRowsetFind](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 Описывает типы даты и времени и **IRowsetFind**.  
 
  
## <a name="see-also"></a>См. также  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
