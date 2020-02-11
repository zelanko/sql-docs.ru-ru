---
title: SQLGetConnectAttr | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 818c136814062c94491cfa02b84d2fff443a1f0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63128667"
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет характерные для драйвера атрибуты соединения. Некоторые атрибуты доступны для `SQLGetConnectAttr`, а функция используется для сообщения о текущих параметрах. Нельзя быть уверенным в правильности значений этих атрибутов, сообщаемых функцией, до тех пор, пока не будет установлено соединение или атрибут не будет задан при помощи функции [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
 В этом разделе приведены атрибуты режима только для чтения. Сведения о других атрибутах подключения, относящихся к драйверу поставщика ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
## <a name="sql_copt_ss_connection_dead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 Атрибут SQL_COPT_SS_CONNECTION_DEAD сообщает серверу данные о состоянии соединения. Для определения текущего состояния соединения драйвер запрашивает сеть.  
  
> [!NOTE]  
>  Стандартный атрибут соединения ODBC SQL_ATTR_CONNECTION_DEAD возвращает последнее по времени состояние соединения. Может оказаться так, что это состояние соединения будет отличаться от текущего.  
  
|Значение|Description|  
|-----------|-----------------|  
|SQL_CD_TRUE|Соединение с сервером потеряно.|  
|SQL_CD_FALSE|Соединение открыто и доступно для обработки инструкций.|  
  
## <a name="sql_copt_ss_client_connection_id"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 Атрибут SQL_COPT_SS_CLIENT_CONNECTION_ID извлекает идентификатор соединения клиента, по которому затем производится поиск и обнаружение следующих данных.  
  
-   Диагностические сведения в журнале XEvents, если он включен.  
  
-   Сведения об ошибке соединения в кольцевом буфере соединения.  
  
-   Диагностические сведения в журналах отслеживания доступа к данным, если они включены.  
  
 Дополнительные сведения см. [в разделе доступ к диагностическим сведениям в журнале расширенных событий](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
|Значение|Description|  
|-----------|-----------------|  
|SQL_ERROR|Ошибка соединения.|  
|SQL_SUCCESS|Подключение выполнено успешно. Идентификатор соединения клиента будет находиться в выходном буфере.|  
  
## <a name="sql_copt_ss_perf_data"></a>SQL_COPT_SS_PERF_DATA  
 Атрибут SQL_COPT_SS_PERF_DATA возвращает указатель на структуру SQLPERF, содержащую текущую статистику производительности драйвера. `SQLGetConnectAttr`Возвращает значение NULL, если ведение журнала производительности не включено. Драйвер не обновляет статистику в структуре SQLPERF динамически. Вызывайте `SQLGetConnectAttr` каждый раз, когда необходимо обновить статистику производительности.  
  
|Значение|Description|  
|-----------|-----------------|  
|NULL|Ведение журнала производительности не включено.|  
|Любое другое значение|Указатель на структуру SQLPERF.|  
  
## <a name="sql_copt_ss_perf_query"></a>SQL_COPT_SS_PERF_QUERY  
 Если запись в журнал данных о длительных запросах включена, то атрибут SQL_COPT_SS_PERF_QUERY возвращает значение TRUE. Если запись в журнал данных о запросах неактивна, этот атрибут возвращает значение FALSE.  
  
## <a name="sql_copt_ss_user_data"></a>SQL_COPT_SS_USER_DATA  
 Атрибут SQL_COPT_SS_USER_DATA извлекает указатель на данные пользователя. Пользовательские данные хранятся в принадлежащей клиенту памяти и записываются отдельно для каждого соединения. Если указатель на данные пользователя на задан, что соответствует значению SQL_UD_NOTSET, то возвращается указатель NULL.  
  
|Значение|Description|  
|-----------|-----------------|  
|SQL_UD_NOTSET|Указатель на данные пользователя не задан.|  
|Любое другое значение|Указатель на данные пользователя.|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>Поддержка функции SQLGetConnectAttr для имен участников-служб (SPN)  
 SQLGetConnectAttr можно использовать для запроса значения новых атрибутов соединения SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD. (SQLGetConnectOption также можно использовать для запроса этих значений.)  
  
 Атрибут SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD доступен только для открытых соединений, в которых используется проверка подлинности Windows.  
  
 Если атрибут SQL_COPT_SS_SERVER_SPN или SQL_COPT_SS_FAILOVER_PARTNER еще не задан, возвращается значение по умолчанию (пустая строка).  
  
 Дополнительные сведения о SPN см. [в статье имена субъектов-служб &#40;имен участников-служб&#41; в клиентских подключениях &#40;&#41;ODBC ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLGetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=59347)   
 [Сведения о реализации API ODBC](odbc-api-implementation-details.md)   
 [Настройка QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)   
 [Настройка ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [Настройка ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [Настройка ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
