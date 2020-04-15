---
title: Картирование типов данных (драйвер ODBC для Oracle) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 432c21b70efcdd63ef36bfe3d26f8488ddb11d1d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302675"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Сопоставление типов данных (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Oracle Server поддерживает набор типов данных. Драйвер ODBC для Oracle отображает эти типы данных в соответствующих типах данных ODBC S'L. В следующей таблице перечислены типы данных Oracle 7.3 Server и соответствующие типы данных ODBC S'L.  
  
 Драйвер ODBC для Oracle поддерживает Oracle 7.3 и некоторые типы данных Oracle8. Для получения дополнительной информации об поддерживаемых типах данных Oracle8 [см.](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
|Тип данных Oracle Server|Тип данных ODBC S'L|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  Для получения дополнительной информации о допустимом размере [VARCHAR Column Size](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) столбца VARCHAR см.
