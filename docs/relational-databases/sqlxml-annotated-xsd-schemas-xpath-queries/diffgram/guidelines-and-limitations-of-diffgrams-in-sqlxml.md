---
title: "Рекомендации и ограничения SQLXML с дельтами | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07f698a9bcd18566d4cca639e810056f79523684
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Рекомендации и действующие ограничения SQLXML, связанные с дельтами
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]При использовании дельт с SQLXML 4.0 следует помните следующее:  
  
-   Типы больших двоичных объектов (BLOB) как **text, ntext** и изображения не должен использоваться в  **\<diffgr: перед >** блока в при работе с Дельтами, так как это будет включать их для использования в Управление параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов **текст** типа данных; Однако такое сравнение завершится ошибкой в случае с типами больших двоичных ОБЪЕКТОВ, где размер данных больше, чем 8 КБ.  
  
-   Специальные символы в **ntext** данных может вызвать проблемы с SQLXML 4.0 из-за ограничений, налагаемых на сравнение типов больших двоичных ОБЪЕКТОВ. Например, использование «[Serializable]» в  **\<diffgr: перед >** блока дельты при проверке столбца параллелизма **ntext** типа будут завершаться следующей SQLOLEDB Описание ошибки:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
