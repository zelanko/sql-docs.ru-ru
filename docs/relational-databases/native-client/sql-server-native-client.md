---
title: SQL Server Native Client | Документация Майкрософт
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 48a335f4cf3dc3990cbcf6bbf68e82ce76a9e54f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73759350"
---
# <a name="sql-server-native-client"></a>собственный клиент SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SNAC или SQL Server Native Client — термин, который используется в качестве взаимозаменяемого, чтобы ссылаться на драйверы ODBC и OLE DB для SQL Server.

> [!IMPORTANT] 
> SQL Server Native Client (SQLNCLI) остается устаревшим и не рекомендуется использовать его для новых задач разработки. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.

> [!NOTE]
> Дополнительные сведения и о загрузке драйверов SNAC или ODBC см. в записи блога, описанной в статье о [жизненном цикле SNAC](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).
> Дополнительные сведения о драйвере ODBC для SQL Server см. в разделе [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).  

 Сведения о функциях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, выпущенных с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], последняя доступная версия SQL Server Native Client:

-   [Поддержка SQL Server Native Client для LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [Доступ к диагностическим сведениям в журнале расширенных событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственном клиенте поддерживает три функции, которые были добавлены в стандартный интерфейс ODBC в пакете SDK для Windows 7:  

-   Асинхронное выполнение операций, связанных с соединением. Дополнительные сведения см. в разделе [Асинхронное выполнение](https://go.microsoft.com/fwlink/?LinkID=191493).  

-   Возможность расширения типа данных C. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  

     Для поддержки этой функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственном клиенте SQLGetDescField может возвращать **SQL_C_SS_TIME2** (для типов **времени** ) или **SQL_C_SS_TIMESTAMPOFFSET** (для **datetimeoffset**) вместо **SQL_C_BINARY**, если приложение использует ODBC 3,8. Дополнительные сведения см. в разделе [Поддержка типов данных для улучшений даты и времени ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  

-   Многократный вызов метода **SQLGetData** с небольшим буфером для получения значения параметра большого объема. Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  

 В следующих разделах описываются изменения поведения собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  

-   При вызове метода **ICommandWithParameters::SetParameterInfo**значение, передаваемое в параметре *pwszName* , должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  

-   **SQLDescribeParam** будет постоянно возвращать значение соответствия спецификации ODBC. Дополнительные сведения см. в разделе [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  

-   [Изменение поведения драйвера ODBC при обработке преобразования символов](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>См. также раздел  
[Установка SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Компоненты собственного клиента SQL Server](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
