---
title: S'LDriverConnect (англ.) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8d1455f0b91313ea137ec9c13a2d318fba0807b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302555"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет атрибуты соединения, которые заменяют или расширяют ключевые слова строки соединения. Некоторые ключевые слова строки соединения имеют значения по умолчанию, заданные в драйвере ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список ключевых слов, доступных в драйвере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC, см. [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
 Для получения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] дополнительной информации о атрибутах соединения и поведении драйвера по умолчанию, см. [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)  
  
 Для обсуждения ключевых слов строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединения, действительных для родного клиента, см. [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
 Когда значение параметра **sLDriverConnect**_DriverCompletion_ является SQL_DRIVER_PROMPT, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_DRIVER_COMPLETE или SQL_DRIVER_COMPLETE_REQUIRED, драйвер Native Client ODBC извлекает значения ключевых слов из отображенного окна диалогов. Если значение ключевого слова передается в строке соединения и пользователь не изменил значение в диалоговом окне, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение из строки соединения. Если значение не определено в строке соединения, а пользователь не присваивает его в диалоговом окне, драйвер использует значение по умолчанию.  
  
 **SLDriverConnect** должен быть предоставлен действительный *WindowHandle,* когда любое значение *DriverCompletion* требует (или может потребовать) отображения окна диалога соединения драйвера. Недопустимый дескриптор возвращает ошибку SQL_ERROR.  
  
 Укажите ключевое слово DRIVER или DSN. Драйвер ODBC использует крайнее левое из этих ключевых слов и пропускает другое, если указаны оба. Если DRIVER указан, или является самым левым из двух, и значение параметра **s LDriverConnect**_DriverCompletion_ является SQL_DRIVER_NOPROMPT, требуется ключевое слово SERVER и соответствующее значение.  
  
 Если задано значение SQL_DRIVER_NOPROMPT, необходимо указать ключевые слова проверки подлинности пользователя вместе с их значениями. Драйвер обеспечивает наличие строки «Trusted_Connection=yes» или обоих ключевых слов UID и PWD.  
  
 Если значение параметра *DriverCompletion* является SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных происходит от строки подключения и либо недействительны, **s'LDriverConnect** возвращается SQL_ERROR.  
  
 Если значение параметра *DriverCompletion* является SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных происходит от определений источника данных ODBC и либо недействительны, **S'LDriverConnect** использует язык по умолчанию или базу данных для указанного идентификатора пользователя и возвращает SQL_SUCCESS_WITH_INFO.  
  
 Если значение параметра *DriverCompletion* SQL_DRIVER_COMPLETE или SQL_DRIVER_PROMPT и если язык или база данных недействительны, **S'LDriverConnect** переотображает диалоговое окно.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLDriverConnect  
 Для получения более подробной информации об [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] использовании **S'LDriverConnect** для подключения к кластеру, [SQL Server Native Client Support for High Availability, Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)см.  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Поддержка SQLDriverConnect для имен участников-служб (SPN)  
 При включении запроса sLDDriverConnect будет использоваться диалоговая коробка ODBC Login. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.  
  
 SLDriverConnect примет новые ключевые слова строки соединения **ServerSPN** и **FailoverPartnerSPN,** и распознает новые атрибуты соединения SQL_COPT_SS_SERVER_SPN и SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Если значение атрибута соединения задано более одного раза, приоритет получает программно установленное значение, а не значение в DSN или строке соединения. Значение DSN имеет приоритет над значением в строке соединения.  
  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Для получения дополнительной информации о SPNs см [&#41;&#40;&#41; &#40;. ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
## <a name="examples"></a>Примеры  
 Следующий вызов иллюстрирует наименьший объем данных, необходимых для **S'LDriverConnect:**  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Следующие строки соединения иллюстрируют минимально необходимые данные, когда значение параметра *DriverCompletion* SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция SLDriverConnect](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [Подробная информация о реализации ODBC API](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [ANSI_NULLS&#41;&#40;&#40;&#41;«Трансакт-СЗЛ»](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [&#41;SET ANSI_PADDING &#40;«Трансакт-СЗЛ»](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS (Transact-SQL)](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
