---
description: Использование функций проверки подлинности операционной системы
title: Использование проверки подлинности операционной системы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94563fee00c979addb6fc088bfb3881763e4d188
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471326"
---
# <a name="using-operating-system-authentication"></a>Использование функций проверки подлинности операционной системы
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Проверка подлинности операционной системы Oracle основана на базовой операционной системе для управления доступом к учетным записям базы данных. Пользователям не нужно вводить пароль при использовании этого типа входа.  
  
 Чтобы воспользоваться этой функцией, укажите в качестве идентификатора пользователя "/" и не указывайте пароль при подключении с помощью любого из следующих API подключения: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)или [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Базы данных Oracle используют службы SQL * NET Authentication для проверки подлинности пользователей, которые вошли в систему. Эта служба хорошо работает, если пользователи входят в Oracle через SQLPlus; Однако если вошедший в систему пользователь является службой, такой как службы IIS, проверка подлинности завершается ошибкой. Это известное ограничение \* проверки подлинности SQL NET и создает следующую ошибку: "[Microsoft] [драйвер ODBC для Oracle] [Oracle] Ora-12641: TNS: не удалось инициализировать службу проверки подлинности".  
  
 Эту проблему можно устранить, изменив файл Склнет. ORA. Этот файл конфигурации обычно хранится в подкаталоге Нетворк\админ домашнего каталога Oracle. Добавьте следующую строку в Склнет. ORA:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
