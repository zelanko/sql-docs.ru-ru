---
title: Родной клиент сервера S'L (OLE DB) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 424565f5eb1b0e9ee0770f988090ecb16788c585
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307285"
---
# <a name="sql-server-native-client-ole-db"></a>Собственный клиент SQL Server (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (S'LNCLI) является низкоуровневым COM API, который используется для доступа к данным. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] рекомендуется для разработки средств, программ и низкоуровневых компонентов, требующих высокой производительности. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] — собственный, высокопроизводительный поставщик, который напрямую обращается к протоколу потока табличных данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обеспечивает поддержку OLE DB для приложений, соединяющихся с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB является поставщиком версии OLE DB 2.0.  
 
> [!IMPORTANT]
> Родной [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] клиент OLE DB (S'LNCLI) по-прежнему является амортизированным, и не рекомендуется использовать его для новых работ по разработке. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание приложения поставщика OLE DB для собственного клиента SQL Server](../../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [Объекты источников данных (OLE DB)](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [Команды](../../../relational-databases/native-client-ole-db-commands/commands.md)  
  
-   [Наборы строк](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
-   [Сохраненные процедуры](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
-   [Большие двоичные объекты и объекты OLE](../../../relational-databases/native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [Таблицы и индексы](../../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [Типы данных (OLE DB)](../../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [Поддержка набора строк схемы &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
-   [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [Улучшения функций даты и времени &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [Большие определяемые пользователем типы данных CLR &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md)  
  
-   [Поддержка FILESTREAM &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [Транзакции](../../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
-   [ошибки](../../../relational-databases/native-client-ole-db-errors/errors.md)  
  
-   [Имена участника-службы (SPN) в клиентских соединениях (OLE DB)](../../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [Поддержка разреженных столбцов &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md)  
  
-   [&#40;Ссылка на&#41;&#41;](../../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [Инструкции по OLE DB](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
