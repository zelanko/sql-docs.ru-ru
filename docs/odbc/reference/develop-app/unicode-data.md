---
title: "Данные в Юникоде | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3bb3278fe83922aee29aa8348d32b3fbc757511
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-data"></a>Данные в Юникоде
Для описания данных, которые хранятся в Юникоде в СУБД представлены типы данных SQL в Юникоде. Тип данных Юникода C предназначена для обеспечения привязки данных в Юникоде буфер приложения. Диспетчер драйверов можно преобразовать данные из типа Юникода C (SQL_C_WCHAR), чтобы сделать его функции с помощью драйвера ANSI.  
  
 ODBC 3.0 или 2. *x* приложения будет всегда выполнять привязку к типам данных ANSI. Для достижения оптимальной производительности приложения ODBC 3.5 (или более поздней версии) необходимо привязать в тип данных C ANSI, если тип столбца SQL ANSI и необходимо привязать к типу данных Юникода C, если тип данных столбца SQL имеет формат Юникода.  
  
 Индикаторы типа SQL в Юникоде, SQL_WCHAR, SQL_WVARCHAR и SQL_WLONGVARCHAR. SQL_WCHAR данных имеет фиксированную строку длиной переменной длины с максимальным объявленный имеет SQL_WVARCHAR и SQL_WLONGVARCHAR имеет переменной длины с максимальным, зависит от источника данных.  
  
 Индикатор типа C Юникода — SQL_C_WCHAR. Это значение по умолчанию для каждого из индикаторов типа SQL в Юникоде. Все типы SQL можно преобразовать в SQL_C_WCHAR, и SQL_C_WCHAR можно преобразовать все типы SQL. Приложение может получать данные в одном из трех способов:  
  
-   Извлечь данные как SQL_C_CHAR.  
  
-   Извлечение данных в виде SQL_C_WCHAR.  
  
-   Объявите данные как SQL_C_TCHAR. Это макрос, который вставляет SQL_C_WCHAR, если приложение компилируется как приложения с поддержкой Юникода или вставляет SQL_C_CHAR, если он компилируется как приложение ANSI.  
  
 SQL_C_TCHAR объявляется в функции следующим образом:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 При компиляции приложения как приложения с поддержкой Юникода *ValueType* аргумент должен быть изменен с SQL_C_TCHAR на SQL_C_WCHAR. Когда приложение компилируется как приложение ANSI *ValueType* аргумент будет изменено на SQL_C_CHAR.  
  
 Драйверы Юникода по-прежнему должны поддерживать типы данных ANSI, включая SQL_CHAR. При работе с драйвером Юникод приложение связывает SQL_CHAR, диспетчер драйверов не сопоставляются SQL_CHAR данных SQL_WCHAR. Драйвер Юникода необходимо принять данных SQL_CHAR.  
  
 Диспетчер драйверов драйвера и имена DSN хранятся в Юникоде и сопоставляет их с ANSI при необходимости. Если символ Юникода не удается сопоставить в символ ANSI (как это может произойти при использовании символов из кодовую страницу, которая не является страницей машинный код компьютера в имена DSN и драйверов), символы, которые не могут быть преобразованы, представляются sup символ по умолчанию plied системой.
