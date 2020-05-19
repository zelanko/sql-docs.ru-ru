---
title: SQLDriverConnect | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5f5ef42a9d04a4d1ae72382f44fdf01b62fc6b14
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706277"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет атрибуты соединения, которые заменяют или расширяют ключевые слова строки соединения. Некоторые ключевые слова строки соединения имеют значения по умолчанию, заданные в драйвере ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список ключевых слов, доступных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвере ODBC для собственного клиента, см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Дополнительные сведения об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] атрибутах подключения и поведении драйверов по умолчанию см. в разделе [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
 Описание ключевых слов строки подключения, допустимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Если параметр `SQLDriverConnect` *DriverCompletion* имеет значение SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE или SQL_DRIVER_COMPLETE_REQUIRED, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента получает значения ключевых слов из отображаемого диалогового окна. Если значение ключевого слова передается в строке соединения и пользователь не изменил значение в диалоговом окне, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение из строки соединения. Если значение не определено в строке соединения, а пользователь не присваивает его в диалоговом окне, драйвер использует значение по умолчанию.  
  
 `SQLDriverConnect`необходимо предоставить допустимый *WindowHandle* , если любое значение *DriverCompletion* требует (или может требовать) Отображение диалогового окна подключения драйвера. Недопустимый дескриптор возвращает ошибку SQL_ERROR.  
  
 Укажите ключевое слово DRIVER или DSN. Драйвер ODBC использует крайнее левое из этих ключевых слов и пропускает другое, если указаны оба. Если параметр DRIVER указан или является крайним левым из двух параметров, а `SQLDriverConnect` значение параметра *DriverCompletion* — SQL_DRIVER_NOPROMPT, требуется ключевое слово Server и соответствующее значение.  
  
 Если задано значение SQL_DRIVER_NOPROMPT, необходимо указать ключевые слова проверки подлинности пользователя вместе с их значениями. Драйвер обеспечивает наличие строки «Trusted_Connection=yes» или обоих ключевых слов UID и PWD.  
  
 Если значение параметра *DriverCompletion* равно SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных поступают из строки подключения и либо являются недопустимыми, и `SQLDriverConnect` возвращает SQL_ERROR.  
  
 Если значение параметра *DriverCompletion* равно SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED и язык или база данных поступают из определений источника данных ODBC и либо являются недопустимыми, `SQLDriverConnect` использует язык по умолчанию или базу данных для указанного идентификатора пользователя и возвращает SQL_SUCCESS_WITH_INFO.  
  
 Если значение параметра *DriverCompletion* равно SQL_DRIVER_COMPLETE или SQL_DRIVER_PROMPT и если язык или база данных являются недопустимыми, повторно `SQLDriverConnect` отображает диалоговое окно.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLDriverConnect  
 Дополнительные сведения об использовании `SQLDriverConnect` для подключения к [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] кластеру см. в разделе [Поддержка высокой доступности и аварийного восстановления в SQL Server Native Client](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Поддержка SQLDriverConnect для имен участников-служб (SPN)  
 Склддриверконнект будет использовать диалоговое окно входа ODBC боксвхен, в котором включен запрос. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.  
  
 SQLDriverConnect примет новые ключевые слова строки подключения `ServerSPN` и и `FailoverPartnerSPN` будет распознавать новые атрибуты соединения SQL_COPT_SS_SERVER_SPN и SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Если значение атрибута соединения задано более одного раза, приоритет получает программно установленное значение, а не значение в DSN или строке соединения. Значение DSN имеет приоритет над значением в строке соединения.  
  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Дополнительные сведения о SPN см. [в статье имена субъектов-служб &#40;имен участников-служб&#41; в клиентских подключениях &#40;&#41;ODBC ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Примеры  
 Следующий вызов иллюстрирует наименьший объем данных, необходимых для `SQLDriverConnect` :  
  
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
  
## <a name="see-also"></a>См. также  
 [Функция SQLDriverConnect](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [Сведения о реализации API ODBC](odbc-api-implementation-details.md)   
 [Настройка ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [Настройка ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [SET ANSI_WARNINGS (Transact-SQL)](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
