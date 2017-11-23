---
title: "Идентификаторы типа SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0565ddfffb5b74344aaa41a1d0dfd243c590850
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sql-type-identifiers"></a>Идентификаторы типов SQL
Каждый источник данных определяет собственные типы данных SQL. ODBC определяет тип идентификаторы и описывает общие характеристики типов данных SQL, которые могут быть связаны с идентификатором каждого типа. Это сопоставление каждого типа данных в источнике данных с идентификатором типа SQL ODBC драйвера.  
  
 Например SQL_CHAR является идентификатор типа для символьный столбец с фиксированной длиной, обычно от 1 до 254 символов. Эти характеристики соответствуют тип данных CHAR, найден в многие источники данных SQL. Таким образом когда приложение обнаруживает, что идентификатор типа для столбца SQL_CHAR, его можно предположить, что, вероятно, посвященные столбца данных типа CHAR. Тем не менее он должен выполнять проверку байтовая длина столбца, что он, находится в диапазоне от 1 до 254 символов; драйвер не SQL источнику данных, например, может сопоставить символов фиксированной длины столбца 500 символов SQL_CHAR или SQL_LONGVARCHAR, так как ни один не точного совпадения.  
  
 ODBC определяет широкий спектр идентификаторы типов SQL. Тем не менее драйвер не требуется использовать все эти идентификаторы. Вместо этого он использует только идентификаторы, он должен предоставлять типы данных SQL, поддерживаемые в базовом источнике данных. Если в источнике данных поддерживает следующие типы данных SQL для какой идентификатор типа не соответствует, драйвер можно определить идентификаторы еще один тип. Дополнительные сведения см. в разделе [типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Полное описание идентификаторы типа SQL см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md) в типах данных приложение D:.
