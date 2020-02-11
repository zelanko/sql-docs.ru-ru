---
title: Улучшения даты и времени (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1dec9e1281d2ff61dcab9312cdf5a7ad1ecb8da3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62866841"
---
# <a name="date-and-time-improvements-ole-db"></a>Улучшения функций даты и времени (OLE DB)
  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты-времени. В этом разделе описывается, как эти новые типы предоставляются как расширения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в собственном клиенте. Общие сведения о поддержке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента для новых типов данных даты и времени см. в разделе [улучшения даты и времени](../native-client/features/date-and-time-improvements.md). Пример см. в разделе [Использование расширенных функций даты и времени &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Дополнительные общие сведения о типах данных даты и времени см. в разделе [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Улучшения поддержки типов данных даты и времени OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Предоставляет сведения о типах OLE DB[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Native Client), поддерживающих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных даты и времени.  
  
 [OLE DB &#40;метаданных&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
 Содержит сведения о `ICommandWithParameters::GetParameterInfo`структуре DBBINDING, `ICommandWithParameters::SetParameterInfo` `IColumnsRowset::GetColumnsRowset`,, и I.`ColumnsInfo::GetColumnInfo` Также содержит сведения об обновлениях OLE DB наборах строк схемы.  
  
 [Привязки и преобразования &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Описывает правила преобразования существующих и новых типов данных между сервером и клиентом.  
  
 [Изменения в ходе операции копирования для расширенных типов даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Новые возможности поддержки API OLE DB для функций даты и времени](ole-db-api-support-for-date-and-time-enhancements.md)  
 Описывает API-интерфейсы OLE DB, поддерживающие расширенные возможности типов даты-времени.  
  
 [Сравнимость для IRowsetFind](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Описывает типы даты-времени и интерфейс `IRowsetFind`.  
  
 [Новые функции даты и времени с предыдущими версиями SQL Server &#40;OLE DB&#41;](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Описывает ожидаемое поведение клиентского приложения, использующего улучшение типы даты и времени, при соединении со старыми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также поведение клиента, скомпилированного со старой версией собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который отправляет команды на сервер, поддерживающий расширенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
