---
title: Пример обзора SQL Server | Документация Майкрософт
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
ms.openlocfilehash: 3f3a7568c0849844526ef5f172bcecc0a5857268
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114332"
---
# <a name="sql-server-browsing-example"></a>Пример просмотра SQL Server
В следующем примере показано, как **SQLBrowseConnect** может использоваться для просмотра подключений, доступных в драйвере для SQL Server. Во-первых, приложение запрашивает маркер подключения:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Затем приложение вызывает **SQLBrowseConnect** и указывает драйвер SQL Server, используя Описание драйвера, возвращенное **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Поскольку это первый вызов **SQLBrowseConnect**, диспетчер драйверов загружает драйвер SQL Server и вызывает функцию **SQLBrowseConnect** драйвера с теми же аргументами, которые он получил от приложения.  
  
> [!NOTE]  
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует `Trusted_Connection=yes` указать в строке подключения вместо сведений об идентификаторе пользователя и пароле.  
  
 Драйвер определяет, что это первый вызов **SQLBrowseConnect** , и возвращает второй уровень атрибутов подключения: сервер, имя пользователя, пароль, имя приложения и идентификатор рабочей станции. Для атрибута Server он возвращает список допустимых имен серверов. Код возврата из **SQLBrowseConnect** — SQL_NEED_DATA. Вот строка результата обзора:  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 За каждым ключевым словом в строке результатов обзора следует двоеточие и одно или несколько слов перед знаком равенства. Эти слова являются понятным именем, которое приложение может использовать для создания диалогового окна. Ключевые слова **app** и **WSID** имеют префикс звездочки, что означает, что они являются необязательными. Ключевые слова **Server**, **UID**и **PWD** не являются префиксами звездочки. для них необходимо указать значения в следующей строке запроса на просмотр. Значением ключевого слова **Server** может быть один из серверов, возвращенных **SQLBrowseConnect** , или имя, предоставленное пользователем.  
  
 Приложение вызывает **SQLBrowseConnect** еще раз, указывая зеленый **сервер и опустив** ключевые слова Application и **WSID** , а также понятные имена пользователей после каждого ключевого слова:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Драйвер пытается подключиться к зеленому серверу. При наличии неустранимых ошибок, таких как пропущенная пара "ключевое слово-значение", **SQLBrowseConnect** возвращает SQL_NEED_DATA и остается в том же состоянии, что и до ошибки. Приложение может вызвать **SQLGetDiagField** или **SQLGetDiagRec** для определения ошибки. Если соединение установлено успешно, драйвер возвращает SQL_NEED_DATA и возвращает строку результатов обзора:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Поскольку атрибуты в этой строке являются необязательными, приложение может опустить их. Однако приложение должно вызвать **SQLBrowseConnect** еще раз. Если в приложении выбрано не указывать имя и язык базы данных, то указывается пустая строка запроса обзора. В этом примере приложение выбирает базу данных pubs и вызывает **SQLBrowseConnect** в последний раз, опустив ключевое слово **языка** и звездочку перед ключевым словом **Database** :  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Поскольку атрибут **Database** является окончательным атрибутом соединения, необходимым для драйвера, процесс обзора завершен, приложение подключено к источнику данных, а **SQLBrowseConnect** возвращает SQL_SUCCESS. **SQLBrowseConnect** также возвращает полную строку подключения в виде строки результатов обзора:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Последняя строка подключения, возвращенная драйвером, не содержит понятные имена пользователей после каждого ключевого слова и не содержит необязательных ключевых слов, не заданных приложением. Приложение может использовать эту строку с **SQLDriverConnect** для повторного подключения к источнику данных в текущем обработчике соединения (после отключения) или подключения к источнику данных с другим маркером соединения. Пример:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
