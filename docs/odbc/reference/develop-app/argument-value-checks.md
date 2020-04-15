---
title: Проверка значения аргумента (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6c6e4de16c4a1a80be893acbc7a1993b375f2fee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298830"
---
# <a name="argument-value-checks"></a>Проверки значения аргумента
Менеджер драйвера проверяет следующие типы аргументов. Если не указано иное, менеджер драйвера возвращает SQL_ERROR за ошибки в значениях аргументов.  
  
-   Среда, соединение и ручки оператора обычно не могут быть нулевыми указателями. Менеджер драйвера возвращает SQL_INVALID_HANDLE, когда он находит нулевую ручку.  
  
-   Требуемые аргументы указателя, такие как *OutputHandlePtr* в **S'LAllocHandle** и *CursorName* в **S'LSetCursorName,** не могут быть нулевыми указателями.  
  
-   Флаги опций, не поддерживающие значения, связанные с драйвером, должны быть юридическим значением. Например, *операция* в **S'LSetPos** должна быть SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE или SQL_ADD.  
  
-   Флаги опций должны быть поддержаны в версии ODBC, поддерживаемой драйвером. Например, *InfoType* в **S'LGetInfo** не может быть SQL_ASYNC_MODE (введен в ODBC 3.0) при вызове драйвера ODBC 2.0.  
  
-   Число столбцов и параметров должно быть больше 0 или больше, чем или равно 0, в зависимости от функции. Водитель должен проверить верхний предел этих значений аргумента на основе текущего набора результатов или оператора S'L.  
  
-   Аргументы длины/индикатора и аргументы длины буфера данных должны содержать соответствующие значения. Например, аргумент, оговариваемый длину имени таблицы в **S'LColumns** *(NameLength3)* должен быть SQL_NTS или значением, превышающее 0; *BufferLength* в **S'LDescribeCol** должен быть больше или равен 0. Водителю также может потребоваться проверить эти аргументы. Например, он может проверить, что *NameLength3* меньше или равен максимальной длине имени таблицы в источнике данных.
