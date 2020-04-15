---
title: Объявление приложения&#39;версии ODBC (ru) Документы Майкрософт
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
ms.openlocfilehash: ba346ed7f7a261446110c5513026d20a86fd3a19
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285234"
---
# <a name="declaring-the-application39s-odbc-version"></a>Объявление приложения&#39;версии ODBC
Прежде чем приложение выделяет соединение, оно должно установить атрибут SQL_ATTR_ODBC_VERSION среды. Этот атрибут гласит, что приложение следует спецификации ODBC *2.x* или ODBC *3.x* при использовании следующих элементов:  
  
-   **СЗЛСТАТС**. Многие значения S'LSTATE отличаются в ODBC *2.x* и ODBC *3.x*.  
  
-   **Идентификаторы типа дата, время и тип метки времени.** В следующей таблице отображается идентификаторы типа для даты, времени и метки времени в ODBC *2.x* и ODBC *3.x*.  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**Идентификаторы типа SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Идентификаторы типа C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _КаталогНаи-Аргумент_  **в S'LTables**. В ODBC *2.x*символы подстановочных знаков («%» и «я») в аргументе *CatalogName* рассматриваются буквально. В ODBC *3.x,* они рассматриваются как подстановочные знаки символов. Таким образом, приложение, которое следует спецификации ODBC *2.x,* не может использовать их в качестве символов подстановочных знаков и не избегает их при использовании их в качестве буквальных знаков. Приложение, которое следует спецификации ODBC *3.x* может использовать их в качестве подстановочных символов или избежать их и использовать их в качестве буквальных. Для получения дополнительной информации смотрите [аргументы в каталоге функции](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Менеджер драйверов ODBC *3.x* и драйверы ODBC *3.x* проверяют версию спецификации ODBC, на которую написано приложение, и реагируют соответствующим образом. Например, если приложение следует спецификации ODBC *2.x* и вызывает **S'L'LExecute** перед вызовом **S'LPrepare,** менеджер драйвера ODBC *3.x* возвращает S'Lstate S1010 (ошибка последовательности функций). Если приложение следует спецификации ODBC *3.x,* менеджер драйвера возвращает S'LSTATE HY010 (ошибка последовательности функций). Для получения дополнительной [информации](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)см.  
  
> [!IMPORTANT]  
>  Приложения, которые следуют спецификации ODBC *3.x,* должны использовать условный код, чтобы избежать использования функциональности, новой для ODBC *3.x* при работе с драйверами ODBC *2.x.* Драйверы ODBC *2.x* не поддерживают функциональность, новую для ODBC *3.x* только потому, что приложение заявляет, что оно следует спецификации ODBC *3.x.* Кроме того, драйверы ODBC *3.x* не перестают поддерживать функциональность, новую для ODBC *3.x* только потому, что приложение заявляет, что оно следует спецификации ODBC *2.x.*
