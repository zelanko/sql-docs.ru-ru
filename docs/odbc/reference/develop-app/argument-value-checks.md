---
title: Проверки значений аргументов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 013c8f80a672ed691e7519b318206c406171cfbc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077109"
---
# <a name="argument-value-checks"></a>Проверки значения аргумента
Диспетчер драйверов проверяет следующие типы аргументов. Если не указано иное, диспетчер драйверов возвращает SQL_ERROR для ошибок в значениях аргументов.  
  
-   Дескрипторы среды, соединения и оператора обычно не могут быть пустыми указателями. Диспетчер драйверов возвращает SQL_INVALID_HANDLE при обнаружении маркера null.  
  
-   Обязательные аргументы указателя, такие как *аутпусандлептр* в **функцию SQLAllocHandle** и *курсорнаме* в **SQLSetCursorName**, не могут быть пустыми указателями.  
  
-   Флаги параметров, которые не поддерживают значения, относящиеся к драйверу, должны быть допустимыми значениями. Например, *Операция* в **SQLSetPos** должна иметь SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE или SQL_ADD.  
  
-   Флаги параметров должны поддерживаться в версии ODBC, поддерживаемой драйвером. Например, *инфотипе* в **SQLGetInfo** не может быть SQL_ASYNC_MODE (введено в ODBC 3,0) при вызове драйвера ODBC 2,0.  
  
-   Номера столбцов и параметров должны быть больше 0 или больше или равны 0 в зависимости от функции. Драйвер должен проверить верхний предел этих значений аргументов на основе текущего результирующего набора или инструкции SQL.  
  
-   Аргументы длины/индикатора и длина буфера данных должны содержать соответствующие значения. Например, аргумент, указывающий длину имени таблицы в **SQLColumns** (*NameLength3*), должен быть SQL_NTS или значение больше 0. *BufferLength* в **SQLDescribeCol** должно быть больше или равно 0. Драйверу также может потребоваться проверить эти аргументы. Например, он может проверить, что *NameLength3* меньше или равен максимальной длине имени таблицы в источнике данных.
