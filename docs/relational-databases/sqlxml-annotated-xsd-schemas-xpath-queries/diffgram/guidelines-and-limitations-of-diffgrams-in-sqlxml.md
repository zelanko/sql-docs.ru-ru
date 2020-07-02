---
title: Рекомендации и действующие ограничения SQLXML, связанные с дельтами
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 113090c317e88d3e9a7e7db2bfcb7d4d14b4ea1f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650067"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Рекомендации и действующие ограничения SQLXML, связанные с дельтами
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  При использовании дельт с SQLXML 4.0 учитывайте следующее.  
  
-   Типы больших двоичных объектов (BLOB), такие как **Text/ntext** и Images, не следует использовать в **\<diffgr:before>** блоке в при работе с дельтами, так как он будет включать их для использования в управлении параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов типа данных **Text** . Однако в случае с типами больших двоичных объектов, где размер данных превышает 8 КБ, сравнение завершится ошибкой.  
  
-   Специальные символы в данных типа **ntext** могут вызвать проблемы с SQLXML 4,0 из-за ограничений на сравнение типов больших двоичных объектов. Например, при использовании "[Serializable]" в **\<diffgr:before>** блоке DiffGram при проверке параллелизма столбца типа **ntext** произойдет сбой со следующим описанием ошибки SQLOLEDB:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
