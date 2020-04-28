---
title: Улучшения функций даты и времени (OLE DB)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7dadb038bcb77ee13abdbead023aed164cbe2a8b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306145"
---
# <a name="date-and-time-improvements-ole-db"></a>Улучшения функций даты и времени (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты-времени. В этом разделе описывается, как эти новые типы предоставляются как расширения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в собственном клиенте. Общие сведения о поддержке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента для новых типов данных даты и времени см. в разделе [улучшения даты и времени](../../relational-databases/native-client/features/date-and-time-improvements.md). Пример их использования см. в статье [Использование улучшенных функций даты и времени (OLE DB)](../../relational-databases/native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Общие сведения о типах данных даты и времени вы найдете в разделе документации [datetime (Transact-SQL)](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Улучшения поддержки типов данных даты и времени OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Предоставляет сведения о типах OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Native Client), поддерживающих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных даты и времени.  
  
 [Метаданные (OLE DB)](https://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
 Содержит сведения о структуре DBBINDING, **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset::GetColumnsRowset** и I**ColumnsInfo::GetColumnInfo**. Также предоставляет сведения об обновлениях наборов строк схем OLE DB.  
  
 [Привязки и преобразования &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Описывает правила преобразования существующих и новых типов данных между сервером и клиентом.  
  
 [Изменения в ходе операции копирования для расширенных типов даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Новые возможности поддержки API OLE DB для функций даты и времени](../../relational-databases/native-client-ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Описывает API-интерфейсы OLE DB, поддерживающие расширенные возможности типов даты-времени.  
  
 [Сравнимость для IRowsetFind](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Описывает типы даты и времени, а также интерфейс **IRowsetFind**.  
  
 [Новые функции даты и времени с предыдущими версиями SQL Server &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Описывает ожидаемое поведение клиентского приложения, использующего улучшение типы даты и времени, при соединении со старыми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также поведение клиента, скомпилированного со старой версией собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который отправляет команды на сервер, поддерживающий расширенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
