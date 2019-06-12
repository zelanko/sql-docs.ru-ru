---
title: Организация пулов соединений с учетом драйвера в ODBC Driver for SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d920d15bb633828dd2ad614c6789f397e229f0b5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797803"
---
# <a name="driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server"></a>Организация пулов соединений с учетом драйвера в ODBC Driver для SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Драйвер ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает [организацию пулов соединений с учетом драйвера](https://msdn.microsoft.com/library/hh405031(VS.85).aspx). В этой статье описываются усовершенствования, внесенные в пул соединений с учетом драйвера в Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на платформе Windows:  
  
-   Независимо от свойств соединения, использующие `SQLDriverConnect`, помещаются в пул, отличный от пула соединений, использующих `SQLConnect`.
- При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и организации пулов соединений с учетом драйвера драйвер не использует контекст безопасности пользователя Windows для текущего потока, чтобы разделить соединения в пуле. Таким образом, если по своим параметрам соединения эквивалентны сценариям олицетворения Windows с проверкой подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и используют те же учетные данные проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для подключения к серверной части, другие пользователи Windows потенциально могут использовать тот же пул подключений. При использовании проверки подлинности Windows и организации пулов соединений с учетом драйвера драйвер использует текущий контекст безопасности пользователя Windows, чтобы разделить соединения в пуле. Таким образом, для сценариев олицетворения Windows различные пользователи Windows не используют совместно одни и те же соединения, даже если эти соединения используют одинаковые параметры.
- При использовании Azure Active Directory и использование пулов соединений с учетом драйвера, драйвер также использует значение проверки подлинности для определения членства в пуле соединений.
  
-   Организация пулов соединений с учетом драйвера предотвращает возвращение плохого соединения из пула.  
  
-   Организация пулов соединений с учетом драйвера распознает атрибуты соединения для конкретного драйвера. Таким образом, если соединение использует `SQL_COPT_SS_APPLICATION_INTENT` значение только для чтения, это соединение получает собственный пул соединений.
-   Параметр `SQL_COPT_SS_ACCESS_TOKEN` атрибут приводит к соединения в пул отдельно 
  
Если один из следующих идентификаторов атрибутов соединения или ключевых слов строки подключения различается между строкой подключения и строкой подключения в пуле, драйвер использует соединение в составе пула. Тем не менее производительность повышается, когда все идентификаторы атрибутов соединения или ключевые слова строки подключения совпадают. Для поиска соответствия соединения в пуле драйвер сбрасывает атрибут. Производительность снижается, поскольку для сброса следующих параметров требуется дополнительный вызов по сети.  
  
-    Если два или более из следующих атрибутов соединения или ключевых слов соединения не совпадают, соединение в составе пула не используется.  
  
  - `Language`  
  - `QuoteId`  
  - `SQL_ATTR_TXN_ISOLATION` 
  - `SQL_COPT_SS_QUOTED_IDENT`  
  
-   Если существует различие в любом из следующих ключевых слов соединения между строкой подключения и строкой подключения в пуле, соединение в составе пула не используется.  
  
    |Ключевое слово|Драйвер ODBC 13|Драйвер ODBC 11|
    |-|-|-|
    |`Address`|Да|Да|
    |`AnsiNPW`|Да|Да|
    |`App`|Да|Да|
    |`ApplicationIntent`|Да|Да|  
    |`Authentication`|Да|нет|
    |`ColumnEncryption`|Да|нет|
    |`Database`|Да|Да|
    |`Encrypt`|Да|Да|  
    |`Failover_Partner`|Да|Да|
    |`FailoverPartnerSPN`|Да|Да|
    |`MARS_Connection`|Да|Да|
    |`Network`|Да|Да|
    |`PWD`|Да|Да|
    |`Server`|Да|Да|
    |`ServerSPN`|Да|Да|
    |`TransparentNetworkIPResolution`|Да|Да|
    |`Trusted_Connection`|Да|Да|
    |`TrustServerCertificate`|Да|Да|
    |`UID`|Да|Да|
    |`WSID`|Да|Да|
    
- Если существует различие в любом из следующих атрибутов соединения между строкой подключения и строкой подключения в пуле, соединение в составе пула не используется.  
  
    |attribute|Драйвер ODBC 13|Драйвер ODBC 11|  
    |-|-|-|  
    |`SQL_ATTR_CURRENT_CATALOG`|Да|Да|
    |`SQL_ATTR_PACKET_SIZE`|Да|Да|
    |`SQL_COPT_SS_ANSI_NPW`|Да|Да|
    |`SQL_COPT_SS_ACCESS_TOKEN`|Да|нет|
    |`SQL_COPT_SS_AUTHENTICATION`|Да|нет|
    |`SQL_COPT_SS_ATTACHDBFILENAME`|Да|Да|
    |`SQL_COPT_SS_BCP`|Да|Да|
    |`SQL_COPT_SS_COLUMN_ENCRYPTION`|Да|нет|
    |`SQL_COPT_SS_CONCAT_NULL`|Да|Да|
    |`SQL_COPT_SS_ENCRYPT`|Да|Да|
    |`SQL_COPT_SS_FAILOVER_PARTNER`|Да|Да|
    |`SQL_COPT_SS_FAILOVER_PARTNER_SPN`|Да|Да|
    |`SQL_COPT_SS_INTEGRATED_SECURITY`|Да|Да|
    |`SQL_COPT_SS_MARS_ENABLED`|Да|Да|
    |`SQL_COPT_SS_OLDPWD`|Да|Да|
    |`SQL_COPT_SS_SERVER_SPN`|Да|Да|
    |`SQL_COPT_SS_TRUST_SERVER_CERTIFICATE`|Да|Да|
    |`SSPROP_AUTH_REPL_SERVER_NAME`|Да|Да|
    |`SQL_COPT_SS_TNIR`|Да|нет|
 
-   Драйвер может сбросить и настроить следующие ключевые слова и атрибуты соединения без выполнения дополнительного вызова по сети. Драйвер сбрасывает эти параметры, чтобы убедиться, что соединение не содержит неверные сведения.  
  
     Эти ключевые слова соединения не учитываются, когда диспетчер драйверов пытается сопоставить соединение с соединением в пуле. (Даже в случае изменения одного из этих параметров существующее соединение можно использовать повторно. Драйвер выполнит сброс параметров по мере необходимости.) Эти атрибуты можно сбросить на стороне клиента, не выполняя дополнительный вызов по сети.  
  
    |Ключевое слово|Драйвер ODBC 13|Драйвер ODBC 11|  
    |-|-|-|  
    |`AutoTranslate`|Да|Да|
    |`Description`|Да|Да|
    |`MultisubnetFailover`|Да|Да|  
    |`QueryLog_On`|Да|Да|
    |`QueryLogFile`|Да|Да|
    |`QueryLogTime`|Да|Да|
    |`Regional`|Да|Да|
    |`StatsLog_On`|Да|Да|
    |`StatsLogFile`|  Да|Да|
  
     При изменении одного из следующих атрибутов соединения можно повторно использовать существующее соединения.  Драйвер выполнит сброс значения по мере необходимости. Драйвер может сбросить эти атрибуты на стороне клиента без выполнения дополнительного вызова по сети.  
  
    |attribute|Драйвер ODBC 13|Драйвер ODBC 11|  
    |-|-|-|  
    |Все атрибуты инструкции|Да|Да|
    |`SQL_ATTR_AUTOCOMMIT`|Да|Да|
    |`SQL_ATTR_CONNECTION_TIMEOUT`|  Да|Да|
    |`SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT`|Да|Да|
    |`SQL_ATTR_LOGIN_TIMEOUT`|Да|Да|
    |`SQL_ATTR_ODBC_CURSORS`|  Да|Да|
    |`SQL_COPT_SS_PERF_DATA`|Да|Да|
    |`SQL_COPT_SS_PERF_DATA_LOG`|Да|Да|
    |`SQL_COPT_SS_PERF_DATA_LOG_NOW`| Да|Да| 
    |`SQL_COPT_SS_PERF_QUERY`|Да|Да|
    |`SQL_COPT_SS_PERF_QUERY_INTERVAL`|Да|Да|
    |`SQL_COPT_SS_PERF_QUERY_LOG`|  Да|Да|
    |`SQL_COPT_SS_PRESERVE_CURSORS`|Да|Да|
    |`SQL_COPT_SS_TRANSLATE`|Да|Да|
    |`SQL_COPT_SS_USER_DATA`|  Да|Да|
    |`SQL_COPT_SS_WARN_ON_CP_ERROR`|Да|Да|  
  
## <a name="see-also"></a>См. также:  
 [Драйвер Microsoft ODBC для SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
