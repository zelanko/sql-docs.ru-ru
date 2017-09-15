---
title: "Проверяет значение аргумента | Документы Microsoft"
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
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0a5a57d03f7f1da36115bd0e69c11c33289547f9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="argument-value-checks"></a>Проверяет значение аргумента
Диспетчер драйверов проверяет следующие типы аргументов. Если не указано иное, диспетчер драйверов возвращает значение SQL_ERROR для ошибок в значения аргументов.  
  
-   Дескрипторы среды, инструкции и соединения обычно не может быть указатели null. Диспетчер драйверов возвращает SQL_INVALID_HANDLE, обнаружив значение null, дескриптор.  
  
-   Обязательные аргументы указателя, такие как *OutputHandlePtr* в **SQLAllocHandle** и *CursorName* в **SQLSetCursorName**, не может быть указатели NULL.  
  
-   Параметр флаги, которые не поддерживают значения, относящиеся к драйверу должно быть допустимое значение. Например *операции* в **SQLSetPos** должно быть SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE или SQL_ADD.  
  
-   Флаги должны поддерживаться в версии поддерживаются драйвером ODBC. Например *свойство* в **SQLGetInfo** не может быть SQL_ASYNC_MODE (появился в ODBC 3.0) при вызове с драйвером ODBC 2.0.  
  
-   Номера столбцов и параметров должны быть больше 0 или больше или равно 0, в зависимости от функции. Драйвер должен проверять верхний предел этих значений аргумента, на основе текущего результирующего набора или инструкции SQL.  
  
-   Длины/индикатора и аргументы длины буфера данных должен содержать соответствующие значения. Например, аргумент, который указывает длину имени таблицы в **SQLColumns** (*NameLength3*) должен быть SQL_NTS или значения больше 0; *BufferLength* в **SQLDescribeCol** должно быть больше или равно 0. Драйвер также может потребоваться проверка этих аргументов. Например, он проверяет, *NameLength3* меньше или равно Максимальная длина имени таблицы в источнике данных.
