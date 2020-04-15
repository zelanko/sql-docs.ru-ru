---
title: Пример просмотра серверов S'L (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b15aa8e3d573660a312fceb5b9100a41f0384d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301985"
---
# <a name="sql-server-browsing-example"></a>Пример просмотра SQL Server
В следующем примере показано, как можно использовать **s'LBrowseConnect** для просмотра соединений, доступных с помощью драйвера для сервера S'L. Во-первых, приложение запрашивает ручку соединения:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Далее приложение вызывает **s'LBrowseConnect** и указывает драйвер сервера S'L, используя описание драйвера, возвращенное **S'LDrivers:**  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Поскольку это первый звонок в **S'LBrowseConnect,** менеджер драйвера загружает драйвер s'L Server и вызывает функцию **драйвера S'LBrowseConnect** с теми же аргументами, которые он получил от приложения.  
  
> [!NOTE]  
>  Если вы подключаетесь к поставщику источников данных, который поддерживает аутентификацию Windows, следует указать `Trusted_Connection=yes` вместо идентификатора пользователя и информацию о паролях в строке соединения.  
  
 Драйвер определяет, что это первый вызов на **S'LBrowseConnect** и возвращает второй уровень атрибутов соединения: сервер, имя пользователя, пароль, имя приложения и идентификатор рабочей станции. Для атрибута сервера он возвращает список действительных имен серверов. Код возврата от **S'LBrowseConnect** SQL_NEED_DATA. Вот строка результата просмотра:  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Каждое ключевое слово в строке результата просмотра сопровождается толстой и одной или нескольких слов перед равным знаком. Эти слова являются удобным именем, которое приложение может использовать для создания диалогового окна. Ключевые слова **APP** и **WSID** префиксированы звездочкой, что означает, что они не являются обязательными. **Ключевые**слова SERVER, **UID**и **PWD** не являются префиксированными звездочкой; значения должны быть поставлены для них в следующей строке запроса просмотра. Значение для ключевого слова **SERVER** может быть одним из серверов, возвращенных **S'LBrowseConnect** или имя, поставляемое пользователем.  
  
 Приложение снова вызывает **s'LBrowseConnect,** указывая зеленый сервер и опуская ключевые слова **APP** и **WSID** и удобные имена после каждого ключевого слова:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Водитель пытается подключиться к зеленому серверу. Если есть какие-либо несмертельные ошибки, такие как отсутствующая пара значения ключевых слов, **S'LBrowseConnect** возвращается SQL_NEED_DATA и остается в том же состоянии, что и до ошибки. Для определения ошибки приложение может вызвать **s'LGetDiagField** или **S'LGetDiagRec.** Если соединение успешно, водитель возвращает SQL_NEED_DATA и возвращает строку результата просмотра:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Поскольку атрибуты в этой строке неявляются, приложение может опустить их. Тем не менее, приложение должно снова позвонить в **S'LBrowseConnect.** Если приложение решает опустить имя и язык базы данных, оно определяет пустую строку запроса просмотра. В этом примере приложение выбирает базу данных пабов и вызывает **s'LBrowseConnect** в последний раз, опуская ключевое слово **LANGUAGE** и звездочку перед ключевым словом **DATABASE:**  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Поскольку атрибут **DATABASE** является конечным атрибутом соединения, требуемым драйвером, процесс просмотра завершен, приложение подключено к источнику данных, а **S'LBrowseConnect** возвращается SQL_SUCCESS. **Кроме того, в** качестве строки результатов просмотра также возвращается полная строка соединения:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Окончательная строка соединения, возвращенная драйвером, не содержит удобных для пользователя имен после каждого ключевого слова и не содержит дополнительных ключевых слов, не указанных приложением. Приложение может использовать эту строку с **помощью S'LDriverConnect** для повторного подключения к источнику данных на текущей ручке соединения (после отключения) или для подключения к источнику данных на другой ручке соединения. Пример:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
