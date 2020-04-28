---
title: Использование Microsoft службы IIS | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c71babf933c2615e6c2464696c1023ccaf53dd7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282473"
---
# <a name="using-microsoft-internet-information-services"></a>Использование служб Microsoft IIS
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Если у вас возникли трудности при подключении из скрипта IIS (особенно при получении ошибки ORA-12641), добавьте следующую строку в файл Склнет. ORA:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Это отключит защищенные сетевые службы, чтобы вы могли подключаться с помощью анонимной проверки подлинности.
