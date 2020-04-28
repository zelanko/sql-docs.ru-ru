---
title: Построение взаимодействующих инструкций SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1eccdef63b7d06a456a07f5f1a9ccad987d2de29
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282523"
---
# <a name="constructing-interoperable-sql-statements"></a>Построение инструкций SQL с поддержкой взаимодействия
Как упоминалось в предыдущих разделах, взаимодействующие приложения должны использовать грамматику ODBC SQL. Однако, помимо использования этой грамматики, некоторые дополнительные проблемы возникают из-за взаимодействующих приложений. Например, что делает приложение, если оно хочет использовать функцию, например внешние объединения, которые не поддерживаются всеми источниками данных?  
  
 На этом этапе средство записи приложения должно принимать некоторые решения о том, какие языковые функции требуются, а какие — необязательные. В большинстве случаев, если конкретный драйвер не поддерживает функцию, необходимую для приложения, приложение просто отказывается запускать с этим драйвером. Однако если эта функция необязательна, приложение может обойти эту функцию. Например, он может отключить эти части интерфейса, позволяющие пользователю использовать эту функцию.  
  
 Чтобы определить, какие функции поддерживаются, приложения начинают с вызова **SQLGetInfo** с параметром SQL_SQL_CONFORMANCE. Уровень соответствия SQL предоставляет приложению широкое представление о том, какой SQL поддерживается. Чтобы уточнить это представление, приложение вызывает **SQLGetInfo** с любым другим параметром. Полный список этих параметров см. в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) . Наконец, **SQLGetTypeInfo** возвращает сведения о типах данных, поддерживаемых источником данных. В следующих разделах перечислены возможные факторы, которые должны отслеживаться приложениями при создании взаимодействующих инструкций SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование каталога и схемы](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Положение каталога](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Заключенные в кавычки идентификаторы](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Регистр идентификатора](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escape-последовательности](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Префиксы и суффиксы литералов](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Маркеры параметров в вызовах процедуры](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Инструкции DDL](../../../odbc/reference/develop-app/ddl-statements.md)
