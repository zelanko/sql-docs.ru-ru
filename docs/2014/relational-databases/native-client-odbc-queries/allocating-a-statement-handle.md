---
title: Выделение дескриптора инструкции | Документы Microsoft
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
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1609155d816e681eb8469069fc6f7efcd3f06528
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190200"
---
# <a name="allocating-a-statement-handle"></a>Выделение дескриптора инструкции
  Прежде чем приложение сможет выполнить инструкцию, оно должно выделить дескриптор инструкции. Это делается путем вызова **SQLAllocHandle** с *HandleType* имеющим значение SQL_HANDLE_STMT и *InputHandle* указывающим на дескриптор соединения.  
  
 Атрибуты инструкции представляют собой характеристики дескриптора инструкции. Атрибуты образца инструкции могут включать закладки и курсор для использования с результирующим набором инструкции. Атрибуты инструкции устанавливаются с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md), и их текущие настройки извлекаются с помощью [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md). Приложению не обязательно устанавливать атрибуты инструкции, все они имеют значения по умолчанию, а некоторые зависят от драйвера.  
  
 При использовании некоторых инструкций ODBC и параметров соединения следует соблюдать осторожность. Вызов [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с *fOption* к элементам управления в параметре задать время ожидания приложения для попытки подключения к времени ожидания во время ожидания для установления соединения (0 Указывает на бесконечное ожидание). Сайты с низким временем ответа могут задать большее значение, чтобы дать приложению достаточно времени для установления соединения. Тем не менее этот интервал должен быть достаточно низким, чтобы дать пользователю ответ в том случае, если драйвер не может установить соединение.  
  
 Вызов **SQLSetStmtAttr** с *fOption* равным SQL_ATTR_QUERY_TIMEOUT задает интервал времени ожидания запроса для защиты сервера и пользователя от долго выполняющихся запросов.  
  
 Вызов **SQLSetStmtAttr** с *fOption* значением sql_attr_max_length параметра ограничивает объем **текст** и **изображения** данных, может получить отдельная инструкция. Вызов **SQLSetStmtAttr** с *fOption* равным SQL_ATTR_MAX_ROWS также ограничивает набор строк с первым *n* строк, если это приложение требует. Обратите внимание, что по значению SQL_ATTR_MAX_ROWS драйвер выполняет инструкцию SET ROWCOUNT на сервере. Это влияет на все [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций, включая триггеры и обновления.  
  
 Соблюдайте осторожность при установке этих параметров. Лучше, если все дескрипторы инструкций в дескрипторе соединения будут иметь одинаковые значения SQL_ATTR_MAX_LENGTH и SQL_ATTR_MAX_ROWS. Если драйвер переключается с одного дескриптора инструкции на другой с разными значениями этих параметров, то он должен для изменения значений формировать соответствующие инструкции SET TEXTSIZE и SET ROWCOUNT. Драйвер не может поместить эти инструкции в один пакет как пользовательские инструкции SQL, поскольку пользовательские инструкции SQL могут содержать инструкцию, которая должна быть первой в пакете. Драйвер должен отправлять инструкции SET TEXTSIZE и SET ROWCOUNT в отдельных пакетах, что приводит к появлению дополнительного обращения к серверу.  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  