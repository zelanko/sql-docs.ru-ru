---
title: Приложение г. типы данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e709c74062e31483b042c3930572fb63ca8c786
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996215"
---
# <a name="appendix-d-data-types"></a>Приложение Г. Типы данных
ODBC определяет два набора типов данных: типы данных SQL и типы данных C. Типы данных SQL указывают тип данных, хранящихся в источнике данных. Типы данных C указывают тип данных, хранящихся в буферах приложений.  
  
 Типы данных SQL определяются каждой СУБД в соответствии со стандартом SQL-92. Для каждого типа данных SQL, указанного в стандарте SQL-92, ODBC определяет идентификатор типа, который представляет собой **#define** значение, передаваемое в качестве аргумента в функциях ODBC или возвращаемое в метаданных результирующего набора. Единственными типами данных SQL-92, не поддерживаемыми ODBC, являются БИТОВЫЕ (тип ODBC SQL_BIT имеет различные характеристики), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE и NATIONAL_CHARACTER. Драйверы отвечают за сопоставление типов данных SQL, относящихся к источнику данных, с идентификаторами типов данных SQL ODBC и специфическими для драйвера идентификаторами типа данных SQL. Тип данных SQL указывается в поле SQL_DESC_CONCISE_TYPE дескриптора реализации.  
  
 ODBC определяет типы данных C и соответствующие им идентификаторы типов ODBC. Приложение указывает тип данных C буфера, который будет принимать данные результирующего набора путем передачи соответствующего идентификатора типа C в аргументе *TargetType* при вызове **SQLBindCol** или **SQLGetData**. Он задает тип C буфера, содержащего параметр инструкции, передавая соответствующий идентификатор типа C в аргументе *ValueType* в вызове **SQLBindParameter**. Тип данных C указывается в поле SQL_DESC_CONCISE_TYPE дескриптора приложения.  
  
> [!NOTE]  
>  Нет специфических для драйвера типов данных C.  
  
 Каждый тип данных SQL соответствует типу данных ODBC C. Перед возвратом данных из источника данных драйвер преобразует его в указанный тип данных C. Перед отправкой данных в источник данных драйвер преобразует его из указанного типа данных C.  
  
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
  
 Описание типов данных ODBC см. [в разделе Типы данных в ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md). Дополнительные сведения о типах данных SQL, относящихся к драйверам, см. в документации по драйверу.
