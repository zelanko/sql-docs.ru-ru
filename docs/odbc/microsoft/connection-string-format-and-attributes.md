---
description: Формат и атрибуты строки подключения
title: Формат и атрибуты строки подключения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connection strings
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53efb4dd010913029185f0cbf27f0991f34815fa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412936"
---
# <a name="connection-string-format-and-attributes"></a>Формат и атрибуты строки подключения
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Вместо использования диалогового окна некоторым приложениям может потребоваться строка подключения, указывающая сведения о соединении с источником данных. Строка подключения состоит из нескольких атрибутов, которые определяют способ подключения драйвера к источнику данных. Атрибут определяет конкретный фрагмент информации, который должен быть определен драйвером, прежде чем он сможет создать соответствующее соединение с источником данных. Каждый драйвер может иметь другой набор атрибутов, но формат строки подключения всегда один и тот же. Строка подключения имеет следующий формат:  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Драйвер Microsoft ODBC для Oracle поддерживает формат строки подключения для первой версии драйвера, который использовался `CONNECTSTRING` вместо `SERVER=` .  
  
 При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать `Trusted_Connection=yes` в строке подключения вместо сведений об идентификаторе пользователя и пароле.  
  
 Необходимо указать имя источника данных, если не указать атрибуты UID, PWD, SERVER (или CONNECTSTRING) и DRIVER. Однако все остальные атрибуты являются необязательными. Если атрибут не указан, то по умолчанию этот атрибут имеет значение, указанное на вкладке соответствующая DSN в диалоговом окне **Администратор источников данных ODBC** . Значение атрибута может быть с учетом регистра.  
  
 Ниже приведены атрибуты для строки подключения.  
  
|attribute|Описание|Значение по умолчанию|  
|---------------|-----------------|-------------------|  
|DSN|Имя источника данных, указанное на вкладке "драйверы" диалогового окна " **Администратор источников данных ODBC** ".|""|  
|PWD|Пароль для сервера Oracle, к которому требуется получить доступ. Этот драйвер поддерживает ограничения, которые поддерживаются в Oracle для паролей.|""|  
|SERVER|Строка подключения для сервера Oracle, к которому требуется получить доступ.|""|  
|ИД пользователя|Имя пользователя сервера Oracle. В зависимости от системы этот атрибут может быть необязательным, то есть некоторые базы данных и таблицы могут потребовать этот атрибут в целях безопасности.<br /><br /> Используйте "/" для использования проверки подлинности операционной системы Oracle.|""|  
|BUFFERSIZE|Оптимальный размер буфера, используемый при выборке столбцов.<br /><br /> Драйвер оптимизирует выборку, чтобы одна выборка из сервера Oracle возвращала достаточное количество строк для заполнения буфера этого размера. Большие значения, как правило, увеличивают производительность при выборке большого объема данных.|65535|  
|синонимколумнс|Если это значение равно true (1), вызов API Склколумн () возвращает сведения о столбце. В противном случае Склколумн () возвращает только столбцы для таблиц и представлений. Драйвер ODBC для Oracle обеспечивает более быстрый доступ, если это значение не задано.|1|  
|ПРИМЕЧАНИЯ|Если это значение равно true (1), драйвер возвращает столбцы комментариев для результирующего набора [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) . Драйвер ODBC для Oracle обеспечивает более быстрый доступ, если это значение не задано.|0|  
|стддайофвик|Обеспечивает стандарт ODBC для скаляра DAYOFWEEK. По умолчанию этот параметр включен, но пользователи, которым требуется локализованная версия, могут изменить поведение для использования любого возвращаемого Oracle.|1|  
|гуесссеколдеф|Указывает, должен ли драйвер возвращать ненулевое значение для аргумента *кбколдеф* параметра **SQLDescribeCol**. Применяется только к столбцам, для которых не определен масштаб Oracle, например вычисленные числовые столбцы и столбцы, определенные как число без точности или масштаба. Вызов **SQLDescribeCol** возвращает 130 для точности, когда Oracle не предоставляет эти сведения.|0|  
  
 Например, строка подключения, которая подключается к источнику данных MyDataSource с помощью сервера Мйораклесервероракле и пользователя Oracle Мюсерид, будет выглядеть так:  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 Строка подключения, которая подключается к источнику данных Мйосердатасаурце с помощью проверки подлинности операционной системы и сервера Мйосерораклесервероракле, будет выглядеть так:  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
