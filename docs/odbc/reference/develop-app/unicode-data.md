---
title: Данные Unicode Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73ea9035b05f04fec1527ca2aa98531a807db8cf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307401"
---
# <a name="unicode-data"></a>Данные в Юникоде
Для описания данных, наиболее на DBMS, предоставляются типы данных СЗЛ Unicode. Для того чтобы приложение привязало данные к буферу Unicode, предоставляется тип данных C Unicode. Менеджер драйвера может конвертировать данные из типа Unicode C (SQL_C_WCHAR), чтобы сделать их функционетом с драйвером ANSI.  
  
 ODBC 3.0 или 2. *приложение x* всегда будет привязываться к типам данных ANSI. Для оптимальной производительности приложение ODBC 3.5 (или выше) должно привязываться к типу данных ANSI C, если тип столбца S'L является ANSI, и должен привязываться к типу данных Unicode C, если тип столбца S'L является Unicode.  
  
 Индикаторами типа S'L Unicode являются SQL_WCHAR, SQL_WVARCHAR и SQL_WLONGVARCHAR. SQL_WCHAR данные имеют фиксированную длину строки, в то время как SQL_WVARCHAR имеет переменную длину с заявленным максимумом и SQL_WLONGVARCHAR имеет переменную длину с максимальной, которая зависит от источника данных.  
  
 Индикатор типа C Unicode является SQL_C_WCHAR. Это по умолчанию для каждого из индикаторов типа S'L Unicode. Все типы S'L могут быть преобразованы в SQL_C_WCHAR, а SQL_C_WCHAR могут быть преобразованы во все типы S'L. Приложение может получить данные одним из трех способов:  
  
-   Извлекать данные как SQL_C_CHAR.  
  
-   Извлекать данные в SQL_C_WCHAR.  
  
-   Объявить данные как SQL_C_TCHAR. Это макрос, который вставляет SQL_C_WCHAR если приложение компилируется как приложение Unicode или вставляет SQL_C_CHAR если оно компилируется как приложение ANSI.  
  
 SQL_C_TCHAR объявляется в функции следующим образом:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Когда приложение будет компилировано как приложение Unicode, аргумент *ValueType* будет изменен с SQL_C_TCHAR на SQL_C_WCHAR. Когда приложение компилируется как приложение ANSI, аргумент *ValueType* будет изменен на SQL_C_CHAR.  
  
 Драйверы Unicode по-прежнему должны поддерживать типы данных ANSI, включая SQL_CHAR. Если приложение, работая с драйвером Unicode, связывается с SQL_CHAR, менеджер драйвера не отображает данные SQL_CHAR на SQL_WCHAR. Водитель Unicode должен принимать данные SQL_CHAR.  
  
 Менеджер драйверов хранит имена драйверов и DSN в Unicode и по мере необходимости отображает их в ANSI. Если символ Unicode не может быть отображен к символу ANSI (как это может произойти, если символы со страницы кода, которая не является родной страницей кода компьютера, используются в именах драйверов и DSN), символы, которые не могут быть преобразованы, представлены символом по умолчанию, поставляемым системой.
