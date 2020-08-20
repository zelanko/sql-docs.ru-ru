---
description: Пример диагностики шлюзов
title: Пример диагностики шлюзов | Документация Майкрософт
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
ms.openlocfilehash: 17e32f0ccdc1b2fbbebb1969083e216ed3371688
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465786"
---
# <a name="gateways-diagnostic-example"></a>Пример диагностики шлюзов
В архитектуре шлюза драйвер отправляет запросы на шлюз, поддерживающий ODBC. Шлюз отправляет запросы СУБД. Поскольку это компонент, который взаимодействует с диспетчером драйверов, драйвер форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если Oracle основан на шлюзе к RDB в Microsoft Open Data Services и если RDB не удалось найти таблицу EMPLOYEE, шлюз может создать это диагностическое сообщение:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Так как в источнике данных произошла ошибка, шлюз добавил префикс для идентификатора источника данных ([RDB]) в диагностическое сообщение. Поскольку шлюз был компонентом, который взаимосвязан с источником данных, он добавил префиксы для своего поставщика ([DEC]) и идентификатор ([шлюз ODS]) в диагностическое сообщение. Он также добавил значение SQLSTATE и код ошибки RDB в начало диагностического сообщения. Это позволяет сохранить семантику собственной структуры сообщений и по-прежнему предоставить драйверу диагностическую информацию ODBC. Драйвер анализирует сведения об ошибке, связанные с инструкцией Error, с помощью шлюза.  
  
 Поскольку драйвер шлюза является компонентом, который взаимодействует с диспетчером драйверов, он использует предыдущее диагностическое сообщение для форматирования и возврата следующих значений из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
