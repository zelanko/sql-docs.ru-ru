---
title: Организация пулов соединений (драйверы Microsoft для PHP для SQL Server) | Документы Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e4a4718a252a13d6634ce7515b0580b8ce19dd6a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Организация пулов соединений (драйверы Майкрософт для PHP для SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ниже перечислены важные замечания об организации пулов соединений в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] использует организацию пулов соединений ODBC.  
  
-   По умолчанию пул соединений включен в Windows. В Linux и Mac OS X соединения заносятся в пул только в том случае, если включен пул соединений для ODBC. Если включен пул соединений и подключиться к серверу, драйвер пытается использовать соединение из пула перед созданием нового. Если в пуле нет эквивалентного соединения, создается новое соединение, которое добавляется в пул. Драйвер определяет эквивалентность соединений путем сравнения строк подключения.  
  
-   При использовании соединения из пула выполняется сброс состояния соединения.  
  
-   После закрытия соединение возвращается в пул.  
  
Дополнительные сведения об использовании пулов подключений см. в разделе [подключений](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="enablingdisabling-connection-pooling"></a>Организация пулов соединений Включение и отключение
### <a name="windows"></a>Windows
Можно принудить драйвер создать новое соединение (вместо поиска эквивалентного соединения в пуле соединений), задав значение *ConnectionPooling* атрибута в строку подключения к **false**  (или 0).  
  
Если *ConnectionPooling* атрибут указан в строке подключения или если он имеет значение **true** (или 1), драйвер создает новое соединение, только если эквивалентного соединения не существует в пул соединений.  
  
Сведения о других атрибутах соединения см. в статье [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-mac-os-x"></a>Linux и Mac OS X
*ConnectionPooling* атрибут не может использоваться для включения или отключения пулов соединений. 

Организация пулов соединений можно включить или отключить, изменив файл odbcinst.ini конфигурации. Чтобы изменения вступили в силу, следует перезагрузить драйвер.

Установка `Pooling` для `Yes` и положительное `CPTimeout`включает значение файла Odbcinst.ini пулов соединений. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
Установка `Pooling` для `No` файла Odbcinst.ini заставляет драйвер создать новое соединение.
```
[ODBC]
Pooling=No
```
  
## <a name="see-also"></a>См. также  
[Практическое руководство. Подключение с использованием проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md)

[Практическое руководство. Подключение с использованием проверки подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
