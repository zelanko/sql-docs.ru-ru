---
title: Пример просмотра SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBrowseConnect function [ODBC], example
- connecting to data source [ODBC], SqlBrowseConnect
- connecting to driver [ODBC], SQLBrowseConnect
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8dc57d738c1d5726d2208b930c5d4fadcd93b39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149316"
---
# <a name="sql-server-browsing-example"></a>Пример просмотра SQL Server
В следующем примере показан как **SQLBrowseConnect** может использоваться для просмотра подключения, доступные с драйвером для SQL Server. Во-первых приложение запрашивает дескриптора соединения:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Далее, приложение вызывает **SQLBrowseConnect** и указывает драйвер SQL Server, используя Описание драйвера, возвращенный **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Так как это первый вызов **SQLBrowseConnect**, диспетчер драйверов загружает драйвер SQL Server и вызывает драйвер **SQLBrowseConnect** функцию с теми же аргументами, полученный от приложение.  
  
> [!NOTE]  
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать `Trusted_Connection=yes` вместо идентификатора и пароля пользователя в строке подключения.  
  
 Драйвер определяет, что это первый вызов **SQLBrowseConnect** и возвращает второй уровень атрибуты соединения: сервера, имя пользователя, пароль, имя приложения и идентификатор рабочей станции. Для атрибута сервера возвращается список действительные имена серверов. Код возврата из **SQLBrowseConnect** является значение SQL_NEED_DATA. Ниже приведен обзор результирующей строки.  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Каждое ключевое слово в результирующей строке обзора следует двоеточие и одно или несколько слов, до знака равенства. Эти слова — понятное имя, которое приложение может использовать для построения диалоговое окно. **Приложения** и **WSID** ключевые слова имеют префикс звездочка, значит, они являются необязательными. **SERVER**, **UID**, и **PWD** ключевые слова не предшествует символ звездочки; значения должны быть предоставлены для них в следующей строке обзора. Значение для **SERVER** ключевое слово может быть один из серверов, возвращаемый **SQLBrowseConnect** или пользовательское имя.  
  
 Приложение вызывает **SQLBrowseConnect** еще раз, указав сервер зеленый и пропуск **приложения** и **WSID** ключевые слова и понятные имена, после каждого ключевого слова:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Драйвер пытается подключиться к серверу зеленый. Если любой устранимых ошибок, таких как пару отсутствует ключевое слово значение **SQLBrowseConnect** возвращает SQL_NEED_DATA и остается в том же состоянии, так как она была до ошибки. Приложение может вызвать **SQLGetDiagField** или **SQLGetDiagRec** для определения ошибки. Если подключение установлено успешно, драйвер возвращает SQL_NEED_DATA и возвращает результирующую строку обзора:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Так как атрибуты в данной строке являются необязательными, приложение можно исключить их. Тем не менее, приложение должно вызвать **SQLBrowseConnect** еще раз. Если приложение не указывайте имя базы данных и язык, он задает строку запроса пустой обзора. В этом примере приложение использует базу данных pubs и вызовы **SQLBrowseConnect** последний раз, опустив **языка** ключевое слово или звездочку перед **базы данных**ключевое слово:  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Так как **базы данных** атрибутом является атрибут окончательный подключения, необходимую драйверу для обзора процесс будет завершен, приложение подключено к источнику данных и **SQLBrowseConnect** Возвращает значение SQL_SUCCESS. **SQLBrowseConnect** также возвращает всю строку подключения как обзор результирующей строки:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Итоговой строки подключения возвращаемых драйвером не содержит понятные имена после каждого ключевого слова, а не должен содержать необязательные ключевые слова, не определяется приложением. Приложение может использовать эту строку с **SQLDriverConnect** для повторного подключения к источнику данных на текущий дескриптор подключения (после отключения) или для подключения к источнику данных на другое подключение дескриптор. Пример:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
