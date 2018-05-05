---
title: Приложение г. типы данных | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 057f8a5333ee8f542f63993b014bfcba64e350df
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="appendix-d-data-types"></a>Приложение г. типы данных
ODBC определяет два набора типов данных: SQL типы данных и типы данных C. Типы данных SQL указывают тип данных данные, хранящиеся в источнике данных. Типы данных C указывает тип данных данные, хранящиеся в буферы приложения.  
  
 Типы данных SQL определяются каждой СУБД в соответствии со стандартом SQL-92. Для каждого типа данных SQL, определенных в стандарте SQL-92, ODBC определяет идентификатор типа, который является **#define** значение передается в качестве аргумента в функции ODBC или возвращаемого в метаданных результирующего набора. Только SQL-92, типы данных, не поддерживаемый ODBC (типа ODBC SQL_BIT имеет разные характеристики) бит, BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE и NATIONAL_CHARACTER. Драйверы отвечают за сопоставление типов данных SQL, определяемые источником данных идентификаторы типа данных ODBC SQL и идентификаторы типа данных для драйвера SQL. В поле SQL_DESC_CONCISE_TYPE дескриптор реализации указывается тип данных SQL.  
  
 ODBC определяет типы данных C и их соответствующие идентификаторы типа ODBC. Приложение указывает тип данных C буфера, который будет получать данные результирующего набора, передав соответствующий код типа C в *TargetType* аргумента в вызове **SQLBindCol** или  **SQLGetData**. Он указывает тип C буфер, содержащий параметр инструкции, передавая идентификатор соответствующего типа C в *ValueType* аргумента в вызове **SQLBindParameter**. Тип данных C указывается в поле SQL_DESC_CONCISE_TYPE дескриптор приложения.  
  
> [!NOTE]  
>  Нет типов данных C специфические для драйвера.  
  
 Каждый тип данных SQL соответствует типу данных ODBC C. Перед возвратом данных из источника данных, драйвер преобразует его в указанный тип данных C. Перед отправкой данных в источник данных, драйвер преобразует его в указанный тип данных C.  
  
 Это приложение содержит следующие разделы.  
  
-   [Использование идентификаторов типов данных](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [Типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [Типы данных C](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [Идентификаторы и дескрипторы типа данных](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [Идентификаторы псевдотипа](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [Передача данных в двоичной форме](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [Рекомендации по использованию интервальных и числовых типов данных](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [Ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [Размер столбца, число десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 Описание типов данных ODBC см. в разделе [типы данных ODBC в](../../../odbc/reference/develop-app/data-types-in-odbc.md). Сведения о типах данных драйвера SQL см. в документации драйвера.
