---
title: Построение совместимых заявлений S'L (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282523"
---
# <a name="constructing-interoperable-sql-statements"></a>Построение инструкций SQL с поддержкой взаимодействия
Как уже упоминалось в предыдущих разделах, совместимые приложения должны использовать грамматику ODBC S'L. Помимо использования этой грамматики, однако, ряд дополнительных проблем сталкиваются с совместимыми приложениями. Например, что делает приложение, если оно хочет использовать функцию, такую как внешние соединения, которая не поддерживается всеми источниками данных?  
  
 На этом этапе автор приложения должен принять некоторые решения о том, какие языковые функции необходимы, а какие необязательны. В большинстве случаев, если конкретный драйвер не поддерживает функцию, требуемую приложением, приложение просто отказывается работать с этим драйвером. Однако, если функция необязательна, приложение может обойти эту функцию. Например, он может отключить те части интерфейса, которые позволяют пользователю использовать функцию.  
  
 Чтобы определить, какие функции поддерживаются, приложения начинают сяпом, вызывая **s'LGetInfo** с опцией SQL_SQL_CONFORMANCE. Уровень соответствия S'L дает приложению широкое представление о том, какое s'L поддерживается. Чтобы уточнить это представление, приложение вызывает **s'LGetInfo** с любым из ряда других вариантов. Полный список этих опций можно получить в описании функции [S'LGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md) Наконец, **sLGetTypeInfo** возвращает информацию о типах данных, поддерживаемых источником данных. В следующих разделах перечисляется ряд возможных факторов, за которыми приложения должны следить при построении совместимых инструкций по S'L.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование каталога и схемы](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Положение каталога](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Заключенные в кавычки идентификаторы](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Регистр идентификатора](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escape-последовательности](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Префиксы и суффиксы литералов](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Маркеры параметров в вызовах процедуры](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Инструкции DDL](../../../odbc/reference/develop-app/ddl-statements.md)
