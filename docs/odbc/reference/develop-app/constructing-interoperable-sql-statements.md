---
title: Конструирование инструкций SQL с поддержкой взаимодействия | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc8072a6d7291a546f0f12256aa4b336da037a83
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281090"
---
# <a name="constructing-interoperable-sql-statements"></a>Построение инструкций SQL с поддержкой взаимодействия
Как упоминалось в предыдущих разделах, с возможностью взаимодействия приложения должны использовать SQL-грамматику ODBC. За использование данной грамматикой, тем не менее, ряд дополнительных проблем все чаще сталкиваются с возможностью взаимодействия приложений. Например что делает приложение? если он хочет использовать функцию, например внешних соединений, который поддерживается не всеми источниками данных  
  
 На этом этапе разработчик приложения следует принять решения о функциях языка являются обязательными, а какие — дополнительными. В большинстве случаев Если драйвер не поддерживает функции, необходимые для приложения, приложение просто отклоняет для запуска с помощью этого драйвера. Тем не менее если компонент не является обязательным, приложение можно обойти функцию. Например он отключите те части интерфейса, которые пользователи могут использовать функцию.  
  
 Чтобы определить, какие функции поддерживаются, запустите приложения, вызвав **SQLGetInfo** с параметром SQL_SQL_CONFORMANCE. Уровень соответствия SQL предоставляет приложению широкое представление, из которых поддерживается SQL. Чтобы уточнить это представление, приложение вызывает **SQLGetInfo** с любым из ряд других параметров. Полный список этих параметров, см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции. Наконец **SQLGetTypeInfo** возвращает сведения о типах данных, поддерживаемых источником данных. В следующих разделах перечислены ряд возможных факторов, которые должны высматривать приложения при построении с возможностью взаимодействия инструкций SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование каталога и схемы](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Положение каталога](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Заключенные в кавычки идентификаторы](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Регистр идентификатора](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escape-последовательности](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Префиксы и суффиксы литералов](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Маркеры параметров в вызовах процедуры](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Инструкции DDL](../../../odbc/reference/develop-app/ddl-statements.md)
