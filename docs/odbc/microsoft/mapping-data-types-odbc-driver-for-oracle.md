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
ms.openlocfilehash: 47646fd6fdf1e8fd16165af1bcfc5e741c6e610f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080746"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Сопоставление типов данных (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Сервер Oracle поддерживает набор типов данных. Драйвер ODBC для Oracle сопоставляет эти типы данных с соответствующими типами данных ODBC SQL. В следующей таблице перечислены типы данных сервера Oracle 7,3 и соответствующие им типы данных ODBC SQL.  
  
 Драйвер ODBC для Oracle поддерживает Oracle 7,3 и некоторые типы данных Oracle8. Дополнительные сведения о поддерживаемых типах данных Oracle8 см. в разделе [Поддерживаемые типы данных](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Тип данных сервера Oracle|Тип данных ODBC SQL|  
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
>  Дополнительные сведения о допустимом размере столбца VARCHAR см. в разделе [размер столбца varchar](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) в этом пошаговом окне.
