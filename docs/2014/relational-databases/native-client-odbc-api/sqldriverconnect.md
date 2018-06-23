---
title: SQLDriverConnect | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
caps.latest.revision: 60
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2e83f19e8834004ebfe0a92f3471645a149332c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193182"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет атрибуты соединения, которые заменяют или расширяют ключевые слова строки соединения. Некоторые ключевые слова строки соединения имеют значения по умолчанию, заданные в драйвере ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список ключевых слов, доступных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] атрибуты соединения и поведении драйвера по умолчанию. в разделе [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
 Описание ключевых слов строки подключения, которые являются допустимыми для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client см. в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Когда `SQLDriverConnect` *DriverCompletion* значение параметра является SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE или SQL_DRIVER_COMPLETE_REQUIRED, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента получает значения ключевых слов из отображается диалоговое окно. Если значение ключевого слова передается в строке соединения и пользователь не изменил значение в диалоговом окне, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение из строки соединения. Если значение не определено в строке соединения, а пользователь не присваивает его в диалоговом окне, драйвер использует значение по умолчанию.  
  
 `SQLDriverConnect` должен быть задан допустимый *WindowHandle* при выполнении *DriverCompletion* значение требует (или может потребовать) отображения диалогового окна соединения драйвера. Недопустимый дескриптор возвращает ошибку SQL_ERROR.  
  
 Укажите ключевое слово DRIVER или DSN. Драйвер ODBC использует крайнее левое из этих ключевых слов и пропускает другое, если указаны оба. Если ДРАЙВЕР указан или является крайнее левое и `SQLDriverConnect` *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT, ключевое слово SERVER и соответствующее значение не требуются.  
  
 Если задано значение SQL_DRIVER_NOPROMPT, необходимо указать ключевые слова проверки подлинности пользователя вместе с их значениями. Драйвер обеспечивает наличие строки «Trusted_Connection=yes» или обоих ключевых слов UID и PWD.  
  
 Если *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED и язык или база данных определяется с помощью строки подключения и другое недопустимы, `SQLDriverConnect` возвращает значение SQL_ERROR.  
  
 Если *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED и язык или база данных поступают из определений источников данных ODBC и недопустимы, `SQLDriverConnect` использует значение по умолчанию язык или база данных для заданного идентификатора пользователя и возвращает значение SQL_SUCCESS_WITH_INFO.  
  
 Если *DriverCompletion* значение параметра является SQL_DRIVER_COMPLETE или SQL_DRIVER_PROMPT, а если язык или база данных является недопустимым, `SQLDriverConnect` заново отобразит диалоговое окно.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLDriverConnect  
 Дополнительные сведения об использовании `SQLDriverConnect` для подключения к [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] кластера см. в разделе [SQL Server Native Client Support для высокого уровня доступности и аварийного восстановления](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Поддержка SQLDriverConnect для имен участников-служб (SPN)  
 SQLDDriverConnect будет использовать имя входа ODBC, включенном приглашении диалогового окна. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.  
  
 SQLDriverConnect будет принимать новые ключевые слова строки подключения `ServerSPN` и `FailoverPartnerSPN`, а также распознает новые атрибуты соединения SQL_COPT_SS_SERVER_SPN и SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Если значение атрибута соединения задано более одного раза, приоритет получает программно установленное значение, а не значение в DSN или строке соединения. Значение DSN имеет приоритет над значением в строке соединения.  
  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Дополнительные сведения об именах SPN см. в разделе [имена участника-службы &#40;имена участников-служб&#41; в клиентских соединениях &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Примеры  
 В следующем вызове показан наименьшего объема данных, необходимых для `SQLDriverConnect`:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Следующей строке соединения показан минимальный объем необходимых данных при *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>См. также  
 [SQLDriverConnect, функция](http://go.microsoft.com/fwlink/?LinkId=59340)   
 [Сведения о реализации API-интерфейса ODBC](odbc-api-implementation-details.md)   
 [SET ANSI_NULLS (Transact-SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [Параметр SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
