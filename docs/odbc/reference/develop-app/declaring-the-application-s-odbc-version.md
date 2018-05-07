---
title: Объявление приложения&#39;s версия ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b68c0d0fc233cbe41d38846048643f7e02f6013b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="declaring-the-application39s-odbc-version"></a>Объявление приложения&#39;s версия ODBC
Перед приложение выделяет соединения, его необходимо задать атрибут SQL_ATTR_ODBC_VERSION среды. Этот атрибут состояний, что приложение следует ODBC 2. *x* или ODBC 3. *x* спецификации при использовании следующих элементов:  
  
-   **Атрибуты SQLSTATE**. Многие значения SQLSTATE отличаются в ODBC 2. *x* и ODBC 3. *x*.  
  
-   **Даты, времени и типа Timestamp идентификаторы**. Ниже приведены идентификаторы типов для даты, времени и данных timestamp в ODBC 2. *x* и ODBC 3. *x*.  
  
    |ODBC 2. *x*|ODBC 3. *x*|  
    |----------------|----------------|  
    |**Идентификаторы типа SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Идентификаторы типов C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   *CatalogName***аргумента в SQLTables**. В ODBC 2. *x*, подстановочные знаки («%» и «_») в *CatalogName* аргумент обрабатываются буквально. В ODBC 3. *x*, они рассматриваются как символы-шаблоны. Таким образом приложение, которое следует за ODBC 2. *x* спецификации нельзя использовать как шаблон символов, а не escape-их при их использовании в качестве литералов. Приложения ODBC 3 ниже. *x* спецификации можно использовать их в качестве подстановочных знаков или escape-, так и использовать их как литералы. Дополнительные сведения см. в разделе [аргументов функций каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 ODBC 3 *.x* диспетчера драйверов, а ODBC 3 *.x* драйверы, проверьте версию спецификации ODBC, в который записывается приложения и отреагировать соответствующим образом. Например, если приложение соответствует ODBC 2. *x* спецификации и вызовы **SQLExecute** перед вызовом **SQLPrepare**, ODBC 3 *.x* диспетчер драйверов возвращает SQLSTATE S1010 () Ошибка последовательности функций). Если приложение соответствует ODBC 3 *.x* спецификации, диспетчер драйверов возвращает SQLSTATE HY010 (функция ошибка последовательности). Дополнительные сведения см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Приложения, выполните ODBC 3. *x* спецификации необходимо использовать код условия не использовать функциональные возможности в ODBC 3. *x* при работе с ODBC 2. *x* драйверы. ODBC 2. *x* драйверы не поддерживают функциональные возможности в ODBC 3. *x* только потому, что приложение объявляет, обусловленные ODBC 3. *x* спецификации. Кроме того ODBC 3. *x* драйверы не прекращение для поддержки функциональных возможностей в ODBC 3. *x* только потому, что приложение объявляет, что он следует ODBC 2. *x* спецификации.
