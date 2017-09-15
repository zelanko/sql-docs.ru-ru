---
title: "Совместимый со стандартами приложения и драйверы | Документы Microsoft"
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
- standards-compliant applications and drivers [ODBC]
- ODBC drivers [ODBC], standards-compliant
- application features are standards-compliant [ODBC]
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1aba299d163aaf9ec14d86740e5d8aa91ddb7b3b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="standards-compliant-applications-and-drivers"></a>Совместимый со стандартами приложений и драйверов
Совместимый со стандартами приложения или драйвера является запрос, который соответствует спецификации Open CAE группы «данных управления: SQL уровня вызова интерфейса (CLI)» и ISO/IEC 9075-3: 1995 интерфейс уровня вызова (E) (SQL/CLI).  
  
 ODBC 3*.x* обеспечивает следующие возможности:  
  
-   Приложения, написанного для спецификации Open Group и ISO CLI будет работать с ODBC 3*.x* драйвера или совместимый со стандартами драйвера при компиляции с ODBC 3*.x* заголовок файлы и связанные с ODBC 3*.x* библиотек, и когда он получает доступ к драйвера, с помощью ODBC 3*.x* диспетчера драйверов.  
  
-   Драйвер, написанный для спецификации Open Group и ISO CLI будет работать с ODBC 3*.x* приложение или приложение стандартам при компиляции с ODBC 3*.x* заголовок файлы и связанные в ODBC 3*.x* библиотеки, и если приложение получает доступ к драйвера, с помощью ODBC 3*.x* диспетчера драйверов.  
  
 Совместимый со стандартами приложения и драйверы, компилируются с помощью флага компиляции ODBC_STD.  
  
 Совместимый со стандартами приложений демонстрируются следующие особенности:  
  
-   Если совместимый со стандартами приложение вызывает **SQLAllocEnv** (что может произойти из-за **SQLAllocEnv** имеет допустимую функцию Open Group и ISO CLI), вызов сопоставляется с ** SQLAllocHandleStd** во время компиляции. В результате во время выполнения, приложение вызывает **SQLAllocHandleStd**. В ходе обработки данного вызова диспетчера драйверов устанавливает атрибут среды SQL_ATTR_ODBC_VERSION значение SQL_OV_ODBC3. Вызов **SQLAllocHandleStd** эквивалентен вызову для **SQLAllocHandle** с *HandleType* SQL_HANDLE_ENV и вызов **SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION присваивается значение SQL_OV_ODBC3.  
  
-   Если совместимый со стандартами приложение вызывает **SQLBindParam** (что может произойти, потому что **SQLBindParam** имеет допустимую функцию Open Group и ISO CLI), ODBC 3*.x* Диспетчер драйверов сопоставляет вызов вызов эквивалентной в **SQLBindParameter**. (См. [SQLBindParam сопоставления](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.)  
  
-   В соответствии с ISO (CLI), ODBC 3*.x* заголовочные файлы содержат псевдонимы для типы сведения, используемые в вызовах **SQLGetInfo**. Совместимый со стандартами приложения можно использовать эти псевдонимы вместо функции ODBC 3*.x* типы информации. Дополнительные сведения см. в разделе Далее [файлы заголовка](../../../odbc/reference/develop-app/header-files.md).  
  
-   Совместимый со стандартами приложения необходимо убедиться, что он поддерживает все функции поддерживаются в программе, которая будет работать с. Присвоение атрибуту инструкции SQL_ATTR_CURSOR_SCROLLABLE SQL_SCROLLABLE и параметр атрибута инструкции SQL_ATTR_CURSOR_SENSITIVITY SQL_INSENSITIVE или SQL_SENSITIVE, возможности, которые могут использоваться в качестве дополнительных функций в стандарты но не включаются в ODBC 3*.x* Core уровень и, следовательно, может не поддерживаться все ODBC 3*.x* драйверы. Если совместимый со стандартами приложение использует эти возможности, его следует убедиться, что драйвер, который будет работать с поддерживает их.
