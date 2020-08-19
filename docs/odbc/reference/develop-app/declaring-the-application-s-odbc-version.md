---
description: Объявление версии ODBC для приложения&#39;s
title: Объявление приложения&#39;s версии ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ff41a7a8b56133b0a44947980805c5b46238bad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424725"
---
# <a name="declaring-the-application39s-odbc-version"></a>Объявление версии ODBC для приложения&#39;s
Прежде чем приложение выделит соединение, оно должно установить атрибут среды SQL_ATTR_ODBC_VERSION. Этот атрибут указывает, что приложение соответствует спецификации ODBC *2. x* или ODBC *3. x* при использовании следующих элементов:  
  
-   **SQLSTATE**. Многие значения SQLSTATE отличаются в ODBC *2. x* и ODBC *3. x*.  
  
-   **Идентификаторы типа даты, времени и метки**времени. В следующей таблице показаны идентификаторы типов данных даты, времени и отметок времени в ODBC *2. x* и ODBC *3. x*.  
  
    |ODBC *2. x*|ODBC *3. x*|  
    |----------------|----------------|  
    |**Идентификаторы типа SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Идентификаторы типов C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   Аргумент _CatalogName_**в SQLTables**.   В ODBC *2. x*подстановочные знаки ("%" и "_") в аргументе *CatalogName* обрабатываются буквально. В ODBC *3. x*они рассматриваются как подстановочные знаки. Таким образом, приложение, следующее за спецификацией ODBC *2. x* , не может использовать их в качестве подстановочных знаков и не будет экранировано их при использовании в качестве литералов. Приложение, следующее за спецификацией ODBC *3. x* , может использовать их в качестве подстановочных знаков или escape-последовательности и использовать их в качестве литералов. Дополнительные сведения см. [в разделе аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Диспетчер драйверов ODBC *3. x* и драйверы ODBC *3. x* ПРОверяют версию спецификации ODBC, в которую записывается приложение, и отвечает соответствующим образом. Например, если приложение соответствует спецификации ODBC *2. x* и вызывает **SQLExecute** перед вызовом **SQLPrepare**, диспетчер драйверов ODBC *3. x* возвращает значение SQLSTATE S1010 (ошибка последовательности функций). Если приложение соответствует спецификации ODBC *3. x* , диспетчер драйверов ВОЗВРАЩАЕТ значение SQLSTATE HY010 (ошибка последовательности функций). Дополнительные сведения см. в разделе [обратная совместимость и соответствие стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Приложения, которые соответствуют спецификации ODBC *3. x* , должны использовать условный код, чтобы не использовать новые возможности ODBC *3. x* при работе с драйверами ODBC *2. x* . Драйверы ODBC *2. x* не поддерживают новые функции ODBC *3. x* , так как приложение объявляет, что оно соответствует спецификации ODBC *3. x* . Более того, драйверы ODBC *3. x* не прекращают поддерживать новые функции ODBC *3. x* , поскольку приложение объявляет, что оно соответствует спецификации ODBC *2. x* .
