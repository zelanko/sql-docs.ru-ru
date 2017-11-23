---
title: "SQLGetConnectAttr | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
caps.latest.revision: "60"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c2a8e5c05177ae4a69c69a0776af333d96575c0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет характерные для драйвера атрибуты соединения. Некоторые из этих атрибутов доступны для функции **SQLGetConnectAttr**, а сама функция используется для определения их текущих значений. Значение, указанное для этих атрибутов не гарантируется до, после установки соединения или атрибут значение [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 В этом разделе приведены атрибуты режима только для чтения. Сведения о других [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] атрибуты подключения драйвера ODBC для собственного клиента, в разделе [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="sqlcoptssconnectiondead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 Атрибут SQL_COPT_SS_CONNECTION_DEAD сообщает серверу данные о состоянии соединения. Для определения текущего состояния соединения драйвер запрашивает сеть.  
  
> [!NOTE]  
>  Стандартный атрибут соединения ODBC SQL_ATTR_CONNECTION_DEAD возвращает последнее по времени состояние соединения. Может оказаться так, что это состояние соединения будет отличаться от текущего.  
  
|Значение|Описание|  
|-----------|-----------------|  
|SQL_CD_TRUE|Соединение с сервером потеряно.|  
|SQL_CD_FALSE|Соединение открыто и доступно для обработки инструкций.|  
  
## <a name="sqlcoptssclientconnectionid"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 Атрибут SQL_COPT_SS_CLIENT_CONNECTION_ID извлекает идентификатор соединения клиента, по которому затем производится поиск и обнаружение следующих данных.  
  
-   Диагностические сведения в журнале XEvents, если он включен.  
  
-   Сведения об ошибке соединения в кольцевом буфере соединения.  
  
-   Диагностические сведения в журналах отслеживания доступа к данным, если они включены.  
  
 Дополнительные сведения см. в разделе [доступ к диагностической информации в журнале расширенных событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
|Значение|Описание|  
|-----------|-----------------|  
|SQL_ERROR|Ошибка соединения.|  
|SQL_SUCCESS|Подключение выполнено успешно. Идентификатор соединения клиента будет находиться в выходном буфере.|  
  
## <a name="sqlcoptssperfdata"></a>SQL_COPT_SS_PERF_DATA  
 Атрибут SQL_COPT_SS_PERF_DATA возвращает указатель на структуру SQLPERF, содержащую текущую статистику производительности драйвера. Если ведение журнала производительности не включено, функция**SQLGetConnectAttr** возвращает значение NULL. Драйвер не обновляет статистику в структуре SQLPERF динамически. Каждый раз, когда возникает необходимость обновить статистику производительности, вызывайте функцию **SQLGetConnectAttr** .  
  
|Значение|Описание|  
|-----------|-----------------|  
|NULL|Ведение журнала производительности не включено.|  
|Любое другое значение|Указатель на структуру SQLPERF.|  
  
## <a name="sqlcoptssperfquery"></a>SQL_COPT_SS_PERF_QUERY  
 Если запись в журнал данных о длительных запросах включена, то атрибут SQL_COPT_SS_PERF_QUERY возвращает значение TRUE. Если запись в журнал данных о запросах неактивна, этот атрибут возвращает значение FALSE.  
  
## <a name="sqlcoptssuserdata"></a>SQL_COPT_SS_USER_DATA  
 Атрибут SQL_COPT_SS_USER_DATA извлекает указатель на данные пользователя. Пользовательские данные хранятся в принадлежащей клиенту памяти и записываются отдельно для каждого соединения. Если указатель на данные пользователя на задан, что соответствует значению SQL_UD_NOTSET, то возвращается указатель NULL.  
  
|Значение|Описание|  
|-----------|-----------------|  
|SQL_UD_NOTSET|Указатель на данные пользователя не задан.|  
|Любое другое значение|Указатель на данные пользователя.|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>Поддержка функции SQLGetConnectAttr для имен участников-служб (SPN)  
 SQLGetConnectAttr может использоваться для запроса значения новых атрибутов соединения SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD. (SQLGetConnectOption может также использоваться для запроса этих значений.)  
  
 Атрибут SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD доступен только для открытых соединений, в которых используется проверка подлинности Windows.  
  
 Если атрибут SQL_COPT_SS_SERVER_SPN или SQL_COPT_SS_FAILOVER_PARTNER еще не задан, возвращается значение по умолчанию (пустая строка).  
  
 Дополнительные сведения об именах SPN см. в разделе [имена участника-службы &#40; Имена участников-служб &#41; в клиентских подключений &#40; ODBC &#41; ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLGetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=59347)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET QUOTED_IDENTIFIER &#40; Transact-SQL &#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [Параметр SET ANSI_WARNINGS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
