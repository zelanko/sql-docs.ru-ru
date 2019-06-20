---
title: Объявление приложения&#39;s версия ODBC | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c5bb124af74d1fa009a61237edb54a9c8baec74
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267684"
---
# <a name="declaring-the-application39s-odbc-version"></a>Объявление приложения&#39;s версия ODBC
Перед приложение выделяет соединение, его необходимо задать атрибут SQL_ATTR_ODBC_VERSION среды. Этот атрибут утверждает, что приложение соответствует ODBC 2. *x* или ODBC 3. *x* спецификации при использовании следующих элементов:  
  
-   **SQLSTATE**. Многие значения SQLSTATE отличаются в ODBC 2. *x* и ODBC 3. *x*.  
  
-   **Дата, время и идентификаторы типа Timestamp**. Ниже приведены идентификаторы типов для даты и времени данных timestamp в ODBC 2. *x* и ODBC 3. *x*.  
  
    |ODBC 2.*x*|ODBC 3.*x*|  
    |----------------|----------------|  
    |**Идентификаторы типа SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Идентификаторы типа C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_**аргумента в SQLTables**. В ODBC 2. *x*, подстановочные знаки («%» и «_») в *CatalogName* аргумент обрабатываются буквально. В ODBC 3. *x*, они рассматриваются как символы-шаблоны. Таким образом приложения, следующий за ODBC 2. *x* спецификации невозможно использовать их в качестве подстановочных символов и escape-последовательности их при их использовании в качестве литералов. Приложения, следующий за ODBC 3. *x* спецификации можно использовать их в качестве подстановочных знаков или escape-, так и использовать их как литералы. Дополнительные сведения см. в разделе [аргументов в функции работы с каталогами](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 ODBC 3 *.x* диспетчера драйверов, а ODBC 3 *.x* драйверы можно проверить версию спецификации ODBC, в который записывается приложения и реагировать соответствующим образом. Например, если приложение ODBC 2. *x* спецификации и вызывает метод **SQLExecute** перед вызовом **SQLPrepare**, ODBC 3 *.x* диспетчер драйверов возвращает SQLSTATE S1010 () Ошибка последовательности функций). Если приложение ODBC 3 *.x* спецификации, диспетчер драйверов возвращает параметром SQLSTATE HY010 (функционировать ошибка последовательности). Дополнительные сведения см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Приложения, использующие ODBC 3. *x* спецификации необходимо использовать условный код следует применять функциональные возможности в ODBC 3. *x* при работе с ODBC 2. *x* драйверы. ODBC 2. *x* драйверы не поддерживают функциональные возможности в ODBC 3. *x* только потому, что приложение объявляет, что в файле ODBC 3. *x* спецификации. Кроме того ODBC 3. *x* драйверы не прекращение для поддержки функциональных возможностей в ODBC 3. *x* только потому, что приложение объявляет, что в файле ODBC 2. *x* спецификации.
