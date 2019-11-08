---
title: SQLDriverConnect | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9a76a653277b7f99ecf88c3b0277617eb053a41c
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73787094"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет атрибуты соединения, которые заменяют или расширяют ключевые слова строки соединения. Некоторые ключевые слова строки соединения имеют значения по умолчанию, заданные в драйвере ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список ключевых слов, доступных в драйвере ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] атрибутах подключения и поведении драйверов по умолчанию см. в разделе [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Описание ключевых слов строки подключения, допустимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Если параметр_DriverCompletion_ SQLDriverConnect имеет значение SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE или SQL_DRIVER_COMPLETE_REQUIRED, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента получает значения ключевых слов из отображаемого диалогового окна. Если значение ключевого слова передается в строке соединения и пользователь не изменил значение в диалоговом окне, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение из строки соединения. Если значение не определено в строке соединения, а пользователь не присваивает его в диалоговом окне, драйвер использует значение по умолчанию.  
  
 **SQLDriverConnect** должен иметь допустимый *WindowHandle* , если любое значение *DriverCompletion* требует (или может требовать) Отображение диалогового окна подключения драйвера. Недопустимый дескриптор возвращает ошибку SQL_ERROR.  
  
 Укажите ключевое слово DRIVER или DSN. Драйвер ODBC использует крайнее левое из этих ключевых слов и пропускает другое, если указаны оба. Если параметр DRIVER указан или является крайним левым из двух параметров, а значение параметра **SQLDriverConnect**_DriverCompletion_ — SQL_DRIVER_NOPROMPT, требуется ключевое слово Server и соответствующее значение.  
  
 Если задано значение SQL_DRIVER_NOPROMPT, необходимо указать ключевые слова проверки подлинности пользователя вместе с их значениями. Драйвер обеспечивает наличие строки «Trusted_Connection=yes» или обоих ключевых слов UID и PWD.  
  
 Если значение параметра *DriverCompletion* равно SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных поступают из строки подключения и либо являются недопустимыми, **SQLDriverConnect** возвращает SQL_ERROR.  
  
 Если значение параметра *DriverCompletion* равно SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных поступают из определений источника данных ODBC и либо являются недопустимыми, **SQLDriverConnect** использует язык по умолчанию или база данных для указанного идентификатора пользователя и возвращает SQL_SUCCESS_WITH_INFO.  
  
 Если значение параметра *DriverCompletion* равно SQL_DRIVER_COMPLETE или SQL_DRIVER_PROMPT и если язык или база данных являются недопустимыми, **SQLDriverConnect** повторно отображает диалоговое окно.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLDriverConnect  
 Дополнительные сведения об использовании **SQLDriverConnect** для подключения к кластеру [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] см. в разделе [Поддержка высокого уровня доступности и аварийного восстановления в SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Поддержка SQLDriverConnect для имен участников-служб (SPN)  
 Склддриверконнект будет использовать диалоговое окно входа ODBC боксвхен, в котором включен запрос. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.  
  
 SQLDriverConnect примет новые ключевые слова строки подключения **ServerSPN** и **FailoverPartnerSPN**и будет распознавать новые атрибуты соединения SQL_COPT_SS_SERVER_SPN и SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Если значение атрибута соединения задано более одного раза, приоритет получает программно установленное значение, а не значение в DSN или строке соединения. Значение DSN имеет приоритет над значением в строке соединения.  
  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Дополнительные сведения о SPN см. [в &#40;разделе имена субъектов&#41; -служб SPN &#40;в&#41;клиентских соединениях ODBC](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Примеры  
 Следующий вызов иллюстрирует наименьший объем данных, необходимых для **SQLDriverConnect**:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Следующие строки подключения иллюстрируют минимальные необходимые данные, если значение параметра *DriverCompletion* равно SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>См. также раздел  
   [функции SQLDriverConnect](https://go.microsoft.com/fwlink/?LinkId=59340)  
 [Сведения о реализации API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [ЗАДАТЬ ANSI_WARNINGS &#40;TRANSACT-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
