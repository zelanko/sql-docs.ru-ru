---
title: Просмотр примера SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLBrowseConnect function [ODBC], example
- connecting to data source [ODBC], SqlBrowseConnect
- connecting to driver [ODBC], SQLBrowseConnect
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc6687becdb9f76a02ee10f87347033f746d3955
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-browsing-example"></a>Пример обозревателя SQL Server
В следующем примере показан способ **SQLBrowseConnect** может использоваться для просмотра подключения, доступные с драйвером для SQL Server. Во-первых приложение запрашивает дескриптора соединения:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Далее, приложение вызывает **SQLBrowseConnect** и задает драйвер SQL Server, с помощью драйвера описания возвращаемых **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Поскольку это первый вызов **SQLBrowseConnect**, диспетчер драйверов драйвер SQL Server загружает и вызывает драйвер **SQLBrowseConnect** функции с теми же аргументами, полученное от приложение.  
  
> [!NOTE]  
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать `Trusted_Connection=yes` вместо идентификатора и пароля пользователя в строке подключения.  
  
 Драйвер определяет, что это первый вызов **SQLBrowseConnect** и возвращает второй уровень атрибуты соединения: сервер, имя пользователя, пароль, имя приложения и идентификатор рабочей станции. Для атрибута сервера возвращается список действительные имена серверов. Код возврата от **SQLBrowseConnect** — SQL_NEED_DATA. Ниже приведен обзор результирующей строки.  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Каждое ключевое слово в результирующей строке обзора следует двоеточие и одно или несколько слов перед знаком равенства. Эти слова — это понятное имя, которое приложение может использовать для построения диалоговое окно. **Приложения** и **WSID** ключевые слова предшествует символ звездочки, это значит, они не являются обязательными. **Сервера**, **UID**, и **PWD** ключевые слова не предшествует символ звездочки; значения для них должны передаваться в строке запроса Далее обзора. Значение для **сервера** ключевое слово может быть один из серверов, возвращаемый **SQLBrowseConnect** или пользовательское имя.  
  
 Приложение вызывает **SQLBrowseConnect** снова, указав сервер зеленый и пропуск **приложения** и **WSID** ключевые слова и понятных имен после каждого ключевого слова:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Драйвер пытается подключиться к серверу зеленый. Если имеются некритичные ошибки, такие как пары отсутствует ключевое слово значение **SQLBrowseConnect** возвращает SQL_NEED_DATA и остается в том же состоянии, в котором он находился до ошибки. Приложение может вызвать **SQLGetDiagField** или **SQLGetDiagRec** для определения ошибки. Если соединение установлено успешно, драйвер возвращает SQL_NEED_DATA и возвращает результирующую строку обзора:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Поскольку в данной строке атрибуты являются необязательными, приложение можно опустить их. Тем не менее, приложение должно вызвать **SQLBrowseConnect** еще раз. Если опустить имя базы данных и язык приложения, он задает строку запроса пустой обзора. В этом примере приложение использует базу данных pubs и вызовы **SQLBrowseConnect** последний раз пропуск **язык** ключевое слово и звездочка перед **базы данных**ключевое слово:  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Поскольку **базы данных** атрибутом является окончательной подключения драйвера, просмотра процесс будет завершен, приложение подключено к источнику данных и **SQLBrowseConnect** Возвращает значение SQL_SUCCESS. **SQLBrowseConnect** также возвращает строку завершения соединения в результирующей строке обзора:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Драйвер возвращает строку окончательного подключения не содержит понятных имен после каждого ключевого слова, а также содержать необязательные ключевые слова не определяется приложением. Приложение может использовать эту строку с **SQLDriverConnect** для повторного подключения к источнику данных для текущего дескриптора соединения (после отключения) или для подключения к источнику данных в дескрипторе другое подключение. Например:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
