---
title: Имена участника-службы (SPN) в клиентских соединениях (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1d60cb30-4c46-49b2-89ab-701e77a330a2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 73d8cb7b88513173d9342d3910e1f2c959d1c42e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="service-principal-names-spns-in-client-connections-odbc"></a>Имена участника-службы в клиентских соединениях (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В данном разделе рассматриваются атрибуты и функции ODBC, поддерживающие имена участника-службы (SPN) в клиентских приложениях. Дополнительные сведения об именах SPN в клиентских приложениях см. в разделе [имени участника-службы & #40; Имя участника-службы & #41; Поддержка в клиентских соединениях](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) и [получить взаимной проверки подлинности Kerberos](../../../relational-databases/native-client-odbc-how-to/get-mutual-kerberos-authentication.md).  
  
## <a name="connection-string-keywords"></a>Ключевые слова в строке подключения  
 Следующие ключевые слова в строках подключения позволяют задавать имена участника-службы в клиентских приложениях.  
  
|Ключевое слово|Значение|  
|-------------|-----------|  
|**ServerSPN**|Имя участника-службы для сервера. Значением по умолчанию является пустая строка, что вынуждает собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать сформированное драйвером имя участника-службы по умолчанию.|  
|**FailoverPartnerSPN**|Имя участника-службы для партнера по обеспечению отработки отказа. Значением по умолчанию является пустая строка, что вынуждает собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать сформированное драйвером имя участника-службы по умолчанию.|  
  
## <a name="connection-attributes"></a>Атрибуты соединения  
 Следующие атрибуты соединения позволяют указать имя участника-службы и запросить метод проверки подлинности в клиентском приложении.  
  
|Название|Тип|Использование|  
|----------|----------|-----------|  
|SQL_COPT_SS_SERVER_SPN<br /><br /> SQL_COPT_SS_FAILOVER_PARTNER_SPN|SQLTCHAR, чтение и запись|Задает имя участника-службы для сервера. Значением по умолчанию является пустая строка, что вынуждает собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать сформированное драйвером имя участника-службы по умолчанию.<br /><br /> Значение этого атрибута можно запрашивать только после его задания программным путем или после открытия соединения. В противном случае будет возвращено значение SQL_ERROR, а в журнал занесена диагностическая запись с кодом SQLState (равным 08003) и сообщением «Соединение не открыто».<br /><br /> При попытке установить этот атрибут при открытом соединении будет возвращено значение SQL_ERROR и в журнал будет занесена диагностическая запись с кодом SQLState (равным HY011) и сообщением «В настоящее время эта операция недопустима».|  
|SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD|SQLTCHAR, только чтение|Возвращает метод проверки подлинности, используемый для соединения. Приложению возвращается значение, которое Windows возвращает собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Возможны следующие значения:<br /><br /> Значение «NTLM», которое возвращается в том случае, если соединение установлено с использованием проверки подлинности NTLM.<br /><br /> Значение «Kerberos», которое возвращается в том случае, если соединение установлено с использованием проверки подлинности Kerberos.<br /><br /> <br /><br /> Этот атрибут можно прочитать только при открытом соединении, использующем проверку подлинности Windows. При попытке считать его до открытия соединения вернется значение SQL_ERROR и в журнал будет записана ошибка с кодом SQLState 08003 и сообщением «Соединение не открыто».<br /><br /> При попытке запросить значение этого атрибута применительно к соединению, в котором не используется проверка подлинности Windows, возвращается значение SQL_ERROR, а в журнал вносится диагностическая запись с кодом SQLState (равным HY092) и сообщением «Недопустимый идентификатор атрибута или параметра (метод SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD доступен только для доверительных соединений)».<br /><br /> Если не удается определить используемый метод проверки подлинности, происходит возврат значения SQL_ERROR и в журнал вносится диагностическая запись с кодом SQLState (равным HY000) и сообщением «Общая ошибка».|  
|SQL_COPT_SS_MUTUALLY_AUTHENTICATED|SQLSMALLINT, только для чтения|Происходит возврат значения SQL_TRUE, если сервер соединения прошел взаимную проверку подлинности; в противном случае возвращается значение SQL_FALSE.<br /><br /> Этот атрибут можно прочитать только при открытом соединении. При попытке считать его до открытия соединения вернется значение SQL_ERROR и в журнал будет записана ошибка с кодом SQLState 08003 и сообщением «Соединение не открыто».<br /><br /> При попытке запросить значение этого атрибута применительно к соединению, в котором не используется проверка подлинности Windows, будет возвращено значение SQL_FALSE.|  
  
## <a name="odbc-function-support-for-specifying-spns"></a>Поддержка задания имен участников-служб с помощью функций ODBC  
 Клиентские приложения и имена участников-служб поддерживаются следующими функциями ODBC.  
  
-   [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
-   [SQLConnect](../../../relational-databases/native-client-odbc-api/sqlconnect.md)  
  
-   [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)  
  
-   [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)  
  
-   [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)  
  
## <a name="see-also"></a>См. также:  
 [Собственный клиент SQL Server & #40; ODBC & #41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
