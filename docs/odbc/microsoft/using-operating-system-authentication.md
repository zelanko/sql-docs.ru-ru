---
title: Использование операционной системы аутентификации Документы Майкрософт
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
ms.openlocfilehash: d6520202bdbc31baf1156531457cb70a98656e88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292844"
---
# <a name="using-operating-system-authentication"></a>Использование функций проверки подлинности операционной системы
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Проверка подлинности операционной системы Oracle опирается на базовую операционную систему для контроля доступа к учетным записям баз данных. Пользователям не нужно вводить пароль при использовании этого типа входа.  
  
 Чтобы воспользоваться этой функцией, укажите "/" в качестве идентификатора пользователя и не укажите пароль при подключении с помощью любого из следующих AAP подключения: [S'LBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [S'LConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), или [S'LDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Базы данных Oracle используют службы аутентификации s'L-Net для проверки подлинности пользователей, которые вошли в систему. Эта услуга хорошо работает, если пользователи вошли в Oracle через S'LPlus; однако, когда зарегистрированный пользователь является такой услугой, как Интернет информационные службы, проверка подлинности не удается. Это известное ограничение\*сетевой аутентификации и производит следующую ошибку: «Драйвер ODBC для Oracle »Oracle»ORA-12641: Служба проверки подлинности TNS:не удалось инициализировать.  
  
 Исправить эту проблему можно, отредактировав файл Sqlnet.ora. Этот файл конфигурации обычно хранится в подкаталоге сети и админа домашнего каталога Oracle. Добавьте следующую строку в sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
