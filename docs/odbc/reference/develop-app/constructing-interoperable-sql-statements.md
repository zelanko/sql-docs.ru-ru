---
title: Создание инструкций SQL с возможностью взаимодействия | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9419a3e242510a0c65ac87f2c1601c59fdafbd8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="constructing-interoperable-sql-statements"></a>Создание инструкций SQL с возможностью взаимодействия
Как упоминалось в предыдущих разделах, с возможностью взаимодействия приложения должны использовать SQL-грамматику ODBC. Помимо с помощью этой грамматике, однако ряд дополнительных проблем характерные для взаимодействующие приложения. Например что делает приложение? Если хочет использовать функцию, например внешние соединения, который поддерживается не всеми источниками данных  
  
 На этом этапе модуль записи приложения необходимо принять решения относительно функций языка являются обязательными, а какие нет. В большинстве случаев Если драйвер не поддерживает компонент, необходимый для приложения, приложение просто отказывается запускать с этого драйвера. Тем не менее если компонент не является обязательным, приложение можно обойти компонент. Например его отключить эти части интерфейса, которые пользователи могут использовать функцию.  
  
 Чтобы определить, какие функции поддерживаются, запуск приложений путем вызова **SQLGetInfo** с параметром SQL_SQL_CONFORMANCE. Уровень соответствия SQL предоставляет приложению широкие представления, из которых поддерживается SQL. Чтобы уточнить это представление, приложение вызывает **SQLGetInfo** с какой-либо другие варианты. Полный список этих параметров см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции. Наконец **SQLGetTypeInfo** возвращает сведения о типах данных, поддерживаемых источником данных. В следующих разделах перечислены ряд возможных факторы, которые следует обратить приложения при построении с возможностью взаимодействия инструкции SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование каталога и схемы](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Положение каталога](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Заключенные в кавычки идентификаторы](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Регистр идентификатора](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escape-последовательности](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Префиксы и суффиксы литералов](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Маркеры параметров в вызовах процедуры](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Инструкции DDL](../../../odbc/reference/develop-app/ddl-statements.md)
