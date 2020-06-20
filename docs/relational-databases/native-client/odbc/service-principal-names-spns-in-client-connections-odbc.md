---
title: Имена субъектов-служб (SPN) в клиенте ODBC
description: Сведения об атрибутах и функциях ODBC, которые поддерживают имена субъектов-служб (SPN) в клиентских приложениях.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 1d60cb30-4c46-49b2-89ab-701e77a330a2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77db02433bfc67f348a5fbac6c195e76bbd1d69a
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950364"
---
# <a name="service-principal-names-spns-in-client-connections-odbc"></a>Имена участника-службы в клиентских соединениях (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В данном разделе рассматриваются атрибуты и функции ODBC, поддерживающие имена участника-службы (SPN) в клиентских приложениях. Дополнительные сведения об именах участников-служб в клиентских приложениях см. в разделе [имя субъекта-службы &#40;SPN&#41; поддержку в клиентских подключениях](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) и [получение взаимной проверки подлинности Kerberos](../../../relational-databases/native-client-odbc-how-to/get-mutual-kerberos-authentication.md).  
  
## <a name="connection-string-keywords"></a>Ключевые слова в строке подключения  
 Следующие ключевые слова в строках подключения позволяют задавать имена участника-службы в клиентских приложениях.  
  
|Ключевое слово|Применение|  
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
 [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
