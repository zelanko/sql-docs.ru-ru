---
title: Выделение ручки заявления (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 85678c5b03a77910c73bd5b8bac8d0e40d52c252
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291612"
---
# <a name="allocating-a-statement-handle"></a>Выделение дескриптора инструкции
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Прежде чем приложение сможет выполнить инструкцию, оно должно выделить дескриптор инструкции. Он делает это, вызывая **S'LAllocHandle** с параметром *HandleType,* установленным для SQL_HANDLE_STMT и *Вхотистого,* указывая на ручку соединения.  
  
 Атрибуты инструкции представляют собой характеристики дескриптора инструкции. Атрибуты образца инструкции могут включать закладки и курсор для использования с результирующим набором инструкции. Атрибуты оператора устанавливаются с [помощью S'LSetStmtAttr,](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)и их текущие настройки извлекаются с помощью [S'LGetStmtAttr.](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) Приложению не обязательно устанавливать атрибуты инструкции, все они имеют значения по умолчанию, а некоторые зависят от драйвера.  
  
 При использовании некоторых инструкций ODBC и параметров соединения следует соблюдать осторожность. Вызов [S'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с *fOption* набор для SQL_ATTR_LOGIN_TIMEOUT контролирует время, что приложение ждет попытки подключения тайм-аут в ожидании, чтобы установить соединение (0 указывает бесконечное ожидание). Сайты с низким временем ответа могут задать большее значение, чтобы дать приложению достаточно времени для установления соединения. Тем не менее этот интервал должен быть достаточно низким, чтобы дать пользователю ответ в том случае, если драйвер не может установить соединение.  
  
 Вызов **S'LSetStmtAttr** с *fOption* набор для SQL_ATTR_QUERY_TIMEOUT устанавливает интервал времени запроса, чтобы помочь защитить сервер и пользователя от длительных запросов.  
  
 Вызов **S'LSetStmtAttr** с *fOption* набор для SQL_ATTR_MAX_LENGTH ограничивает количество **текстовых** и **изображений** данных, которые отдельные оператора могут получить. Вызов **S'LSetStmtAttr** с *fOption* набор для SQL_ATTR_MAX_ROWS также ограничивает ряды до первого *n* строки, если это все приложение требует. Обратите внимание, что по значению SQL_ATTR_MAX_ROWS драйвер выполняет инструкцию SET ROWCOUNT на сервере. Это влияет [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на все операторы, включая триггеры и обновления.  
  
 Соблюдайте осторожность при установке этих параметров. Лучше, если все дескрипторы инструкций в дескрипторе соединения будут иметь одинаковые значения SQL_ATTR_MAX_LENGTH и SQL_ATTR_MAX_ROWS. Если драйвер переключается с одного дескриптора инструкции на другой с разными значениями этих параметров, то он должен для изменения значений формировать соответствующие инструкции SET TEXTSIZE и SET ROWCOUNT. Драйвер не может поместить эти инструкции в один пакет как пользовательские инструкции SQL, поскольку пользовательские инструкции SQL могут содержать инструкцию, которая должна быть первой в пакете. Драйвер должен отправлять инструкции SET TEXTSIZE и SET ROWCOUNT в отдельных пакетах, что приводит к появлению дополнительного обращения к серверу.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение запросов &#40;&#41;ODBC](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
