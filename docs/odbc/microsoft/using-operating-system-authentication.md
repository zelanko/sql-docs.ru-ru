---
title: С помощью проверки подлинности операционной системы | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a532c253ea2204fa3636c24c503cbefd3fa6311
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127815"
---
# <a name="using-operating-system-authentication"></a>Использование функций проверки подлинности операционной системы
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Проверка подлинности Oracle операционной системы зависит от операционной системы для управления доступом к учетным записям базы данных. Пользователи не должны ввести пароль, при использовании этого типа входа.  
  
 Чтобы воспользоваться преимуществами этой функции, укажите «/» в качестве идентификатора пользователя и пароль не указан, при подключении с помощью любого из следующих подключения API-интерфейсы: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), или [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Баз данных Oracle с помощью SQL * Net службы проверки подлинности для проверки подлинности пользователей, которые вошли в систему. Эта служба работает также в том случае, если пользователи вошли в Oracle через SQLPlus; Тем не менее вошедшего в систему пользователя — это служба, таких как службы IIS, проверка подлинности завершается. Это известное ограничение SQL\*Net проверки подлинности и выдаст следующую ошибку: «[Microsoft] [драйвер ODBC для Oracle] [Oracle] ORA-12641: TNS:Authentication службе не удалось инициализировать.»  
  
 Эту проблему можно решить, изменив файл Sqlnet.ora. Этот файл конфигурации обычно хранятся в подкаталоге Network\Admin Oracle домашнего каталога. Добавьте следующую строку Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
