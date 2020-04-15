---
title: Шлюзы Диагностический пример (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18fd78be7be2eb79316339cbdf3d315deb194fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305575"
---
# <a name="gateways-diagnostic-example"></a>Пример диагностики шлюзов
В архитектуре шлюза драйвер отправляет запросы на шлюз, поддерживающий ODBC. Шлюз отправляет запросы в DBMS. Поскольку именно компонент взаимодействует с менеджером драйвера, драйвер форматирует и возвращает аргументы для **S'LGetDiagRec.**  
  
 Например, если Oracle основывает шлюз rdb на службах открытых данных Майкрософт и если Rdb не сможет найти таблицу EMPLOYEE, шлюз может создать это диагностическое сообщение:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Поскольку ошибка произошла в источнике данных, шлюз добавил префикс для идентификатора источника данных (Rdb) в диагностическое сообщение. Поскольку шлюз был компонентом, который взаимодействовал с источником данных, он добавил префиксы для своего поставщика («DEC») и идентификатор («ODS Gateway») к диагностическому сообщению. Кроме того, к началу диагностического сообщения было добавлено значение S'LSTATE и код ошибки Rdb. Это позволило ему сохранить семантику собственной структуры сообщений и по-прежнему поставлять диагностическую информацию ODBC водителю. Водитель разбирает информацию об ошибке, приложенную к заявлению об ошибке шлюзом.  
  
 Поскольку драйвер шлюза является компонентом, который взаимодействует с менеджером драйвера, он будет использовать предыдущее диагностическое сообщение для формата и возврата следующих значений из **S'LGetDiagRec:**  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
