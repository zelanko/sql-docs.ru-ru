---
title: "Выделение дескриптора инструкции | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 307e65568876acafb2d5c2936302e586fbcb1768
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="allocating-a-statement-handle"></a>Выделение дескриптора инструкции
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Прежде чем приложение сможет выполнить инструкцию, оно должно выделить дескриптор инструкции. Это делается путем вызова **SQLAllocHandle** с *HandleType* имеющим значение SQL_HANDLE_STMT и *InputHandle* указывающим на дескриптор соединения.  
  
 Атрибуты инструкции представляют собой характеристики дескриптора инструкции. Атрибуты образца инструкции могут включать закладки и курсор для использования с результирующим набором инструкции. Атрибуты инструкции устанавливаются с помощью [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md), и их текущие настройки извлекаются с помощью [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md). Приложению не обязательно устанавливать атрибуты инструкции, все они имеют значения по умолчанию, а некоторые зависят от драйвера.  
  
 При использовании некоторых инструкций ODBC и параметров соединения следует соблюдать осторожность. Вызов [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с *fOption* к элементам управления в параметре задать время ожидания приложения для попытки подключения к времени ожидания во время ожидания для установления соединения (0 Указывает на бесконечное ожидание). Сайты с низким временем ответа могут задать большее значение, чтобы дать приложению достаточно времени для установления соединения. Тем не менее этот интервал должен быть достаточно низким, чтобы дать пользователю ответ в том случае, если драйвер не может установить соединение.  
  
 Вызов **SQLSetStmtAttr** с *fOption* равным SQL_ATTR_QUERY_TIMEOUT задает интервал времени ожидания запроса для защиты сервера и пользователя от долго выполняющихся запросов.  
  
 Вызов **SQLSetStmtAttr** с *fOption* значением sql_attr_max_length параметра ограничивает объем **текст** и **изображения** данных, может получить отдельная инструкция. Вызов **SQLSetStmtAttr** с *fOption* равным SQL_ATTR_MAX_ROWS также ограничивает набор строк с первым  *n*  строк, если это приложение требует. Обратите внимание, что по значению SQL_ATTR_MAX_ROWS драйвер выполняет инструкцию SET ROWCOUNT на сервере. Это влияет на все [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций, включая триггеры и обновления.  
  
 Соблюдайте осторожность при установке этих параметров. Лучше, если все дескрипторы инструкций в дескрипторе соединения будут иметь одинаковые значения SQL_ATTR_MAX_LENGTH и SQL_ATTR_MAX_ROWS. Если драйвер переключается с одного дескриптора инструкции на другой с разными значениями этих параметров, то он должен для изменения значений формировать соответствующие инструкции SET TEXTSIZE и SET ROWCOUNT. Драйвер не может поместить эти инструкции в один пакет как пользовательские инструкции SQL, поскольку пользовательские инструкции SQL могут содержать инструкцию, которая должна быть первой в пакете. Драйвер должен отправлять инструкции SET TEXTSIZE и SET ROWCOUNT в отдельных пакетах, что приводит к появлению дополнительного обращения к серверу.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение запросов &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
