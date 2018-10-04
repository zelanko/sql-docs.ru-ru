---
title: Дата и время усовершенствования (OLE DB) | Документация Майкрософт
ms.custom: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 89dc55ce178071245fa6b882625daf0d7c2c49cd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706834"
---
# <a name="date-and-time-improvements-ole-db"></a>Улучшения функций даты и времени (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты-времени. В этом разделе описывается, каким образом эти новые типы доступны в виде расширений в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Общие сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддержки собственным клиентом новые типы даты и времени данных, см. в разделе [время улучшения функций даты и](../../relational-databases/native-client/features/date-and-time-improvements.md). Пример, см. в разделе [использования улучшенных возможностей даты и времени &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Более общие сведения о типах данных даты и времени см. в разделе [datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Улучшения поддержки типов данных даты и времени OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Предоставляет сведения о OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client), поддерживающих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных даты и времени.  
  
 [Метаданные &#40;OLE DB&#41;](http://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
 Содержит сведения о структуре DBBINDING **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset:: GetColumnsRowset**и я**ColumnsInfo::GetColumnInfo**. Также предоставляет сведения об обновлениях наборов строк схем OLE DB.  
  
 [Привязки и преобразования &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Описывает правила преобразования существующих и новых типов данных между сервером и клиентом.  
  
 [Выполнено массовое копирование изменений для типов усиленной даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Новые возможности поддержки API OLE DB для функций даты и времени](../../relational-databases/native-client-ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Описывает API-интерфейсы OLE DB, поддерживающие расширенные возможности типов даты-времени.  
  
 [Сравнимость для IRowsetFind](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Описывает типы даты и времени и **IRowsetFind**.  
  
 [Новые функции даты и времени с предыдущими версиями SQL Server &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Описывает ожидаемое поведение клиентского приложения, использующего улучшение типы даты и времени, при соединении со старыми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также поведение клиента, скомпилированного со старой версией собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который отправляет команды на сервер, поддерживающий расширенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
