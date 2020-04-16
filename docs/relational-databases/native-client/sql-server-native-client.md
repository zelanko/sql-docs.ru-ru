---
title: Сведения
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d175942c9d636221868ca12743e6dac79bb2ddcb
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388718"
---
# <a name="sql-server-native-client"></a>собственный клиент SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SNAC, или Родной клиент сервера S'L, — это термин, который используется как взаимозаменяемый для обозначения драйверов ODBC и OLE DB для S'L Server.

> [!IMPORTANT] 
> Родной клиент сервера S'L (S'LNCLI) по-прежнему является амортизированным, и не рекомендуется использовать его для новых работ по разработке. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.

> [!NOTE]
> Для получения дополнительной информации и скачать SNAC или ODBC Драйверы, см [SNAC жизненный цикл объяснил блоге](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).
> Для получения более подробной информации о [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)драйвере ODBC для сервера S'L, см.  

 Информация [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] о функциях [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Native Client, выпущенная с помощью последней доступной версии родного клиента S'L Server:

-   [Поддержка SQL Server Native Client для LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [Доступ к диагностическим сведениям в журнале расширенных событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Native Client поддерживает три функции, которые были добавлены в стандартный ODBC в Windows 7 SDK:  

-   Асинхронное выполнение операций, связанных с соединением. Дополнительные сведения см. в разделе [Асинхронное выполнение](https://go.microsoft.com/fwlink/?LinkID=191493).  

-   Возможность расширения типа данных C. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  

     Для поддержки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этой функции в Native Client, S'LGetDesccField может вернуть **SQL_C_SS_TIME2** (для типов **времени)** или **SQL_C_SS_TIMESTAMPOFFSET** (для **timetimeoffset)** вместо **SQL_C_BINARY,** если ваше приложение использует ODBC 3.8. Для получения дополнительной информации [см.](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  

-   Многократный вызов метода **SQLGetData** с небольшим буфером для получения значения параметра большого объема. Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  

 В следующих разделах описываются изменения поведения собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  

-   При вызове метода **ICommandWithParameters::SetParameterInfo**значение, передаваемое в параметре *pwszName* , должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  

-   **SLDescribeParam** будет последовательно возвращать спецификацию ODBC, соответствующую значению. Дополнительные сведения см. в разделе [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  

-   [Изменение поведения драйвера ODBC при обработке преобразования символов](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>См. также раздел  
[Установка родного клиента сервера S'L](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Компоненты собственного клиента SQL Server](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
