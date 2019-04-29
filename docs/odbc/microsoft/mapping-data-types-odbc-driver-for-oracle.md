---
title: Сопоставление типов данных (драйвер ODBC для Oracle) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecdd7d7d4b597c4cae218e18b40b0f78e27a6bd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026884"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Сопоставление типов данных (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Сервер Oracle поддерживает набор типов данных. Драйвер ODBC для Oracle сопоставляет эти типы данных в соответствующие типы данных ODBC SQL. Ниже перечислены типы данных Oracle 7.3 Server и соответствующие им типы данных ODBC SQL.  
  
 Драйвер ODBC для Oracle поддерживает Oracle 7.3 и некоторые типы данных Oracle8. Дополнительные сведения о поддерживаемых типах данных Oracle8 см. в разделе [поддерживаемые типы данных](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Тип данных Oracle Server|Тип данных ODBC SQL|  
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
>  Дополнительные сведения о допустимый размер столбца VARCHAR, см. в разделе [размер столбца VARCHAR](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) в данном руководстве.
