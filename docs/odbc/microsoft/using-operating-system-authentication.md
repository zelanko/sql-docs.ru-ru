---
title: "С помощью проверки подлинности операционной системы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3fbe8f4ce9fe9edbb88c7c895311bd9560dc28f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-operating-system-authentication"></a>С помощью проверки подлинности операционной системы
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Проверка подлинности Oracle операционной системы зависит от операционной системы для управления доступом к базе данных учетных записей. Пользователи не должны ввести пароль при использовании этого типа входа.  
  
 Чтобы воспользоваться этой функцией, укажите «/» как идентификатор пользователя и пароль не указан, при подключении с использованием любого из API-интерфейсы следующее подключение: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), или [ SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Баз данных Oracle с помощью SQL * Net службы проверки подлинности для проверки подлинности пользователей, которые вошли в систему. Эта служба работает также в том случае, если пользователи входят в Oracle через SQLPlus; Однако если вошедшего в систему пользователя — это служба, таких как службы IIS, происходит сбой проверки подлинности. Это известное ограничение SQL\*сетевой проверки подлинности и выдаст следующую ошибку: «[Microsoft] [драйвер ODBC для Oracle] [Oracle] ORA-12641: Сбой при инициализации службы TNS:authentication.»  
  
 Эту проблему можно устранить, изменив файл Sqlnet.ora. Этот файл конфигурации обычно хранятся в подкаталоге Network\Admin в домашнем каталоге Oracle. Добавьте следующую строку Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
