---
title: 'Приложение D: Типы данных Документы Майкрософт'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c1abadb962e3a1ee9327bbb8d84e52d180b4a7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292464"
---
# <a name="appendix-d-data-types"></a>Приложение Г. Типы данных
ODBC определяет два типа данных: типы данных S'L и типы данных C. Типы данных S'L указывают тип данных, хранящихся в источнике данных. Типы данных C указывают тип данных, хранящихся в буферах приложений.  
  
 Типы данных S'L определяются каждым DBMS в соответствии со стандартом S'L-92. Для каждого типа данных, указанных в стандарте S'L-92, ODBC определяет идентификатор типа, который является **#define** значением, которое передается в качестве аргумента в функциях ODBC или возвращается в метаданные набора результатов. Единственными типами данных S-L-92, не поддерживаемыми ODBC, являются BIT (тип ODBC SQL_BIT имеет различные характеристики), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE и NATIONAL_CHARACTER. Водители несут ответственность за отображение типов данных, конкретных источников данных СЗЛ, в идентификаторах типа данных ODBC S'L и идентификаторах типа данных, специфичных для драйверов. Тип данных S'L указан в SQL_DESC_CONCISE_TYPE поле дескриптора реализации.  
  
 ODBC определяет типы данных C и соответствующие идентификаторы типа ODBC. Приложение определяет тип данных C буфера, который будет получать данные набора результатов, передавая соответствующий идентификатор типа C в аргументе *TargetType* в вызове на **S'LBindCol** или **S'LGetData.** Он определяет тип C буфера, содержащий параметр оператора, передавая соответствующий идентификатор типа C в аргументе *ValueType* в вызове к **S'LBindParameter.** Тип данных C указан в SQL_DESC_CONCISE_TYPE поле дескриптора приложения.  
  
> [!NOTE]  
>  Нет типов данных C, специфичным для драйверов.  
  
 Каждый тип данных S'L соответствует типу данных ODBC C. Перед возвращением данных из источника данных водитель преобразует их в указанный тип данных C. Перед отправкой данных в источник данных водитель преобразует их из указанного типа данных C.  
  
 Это приложение содержит следующие темы.  
  
-   [Использование идентификаторов типов данных](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [Типы данных S'L](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [Типы данных C](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [Идентификаторы и дескрипторы типа данных](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [Идентификаторы псевдотипа](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [Передача данных в двоичной форме](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [Рекомендации по использованию интервальных и числовых типов данных](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [Ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [Размер столбца, число десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 Для объяснения типов данных ODBC [см.](../../../odbc/reference/develop-app/data-types-in-odbc.md) Для получения информации о типах данных, специфичных для драйверов, просмотрите документацию водителя.
