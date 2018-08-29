---
title: Рекомендации и действующие ограничения SQLXML с Дельтами | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5d0f0ddb4d66aad9280462cf4db595b356e0dc76
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110396"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Рекомендации и действующие ограничения SQLXML, связанные с дельтами
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При использовании дельт с SQLXML 4.0 учитывайте следующее.  
  
-   Типы больших двоичных объектов (BLOB) как **text/ntext** и не следует использовать образы в  **\<diffgr: перед >** блока в при работе с Дельтами, поскольку это будет включать их для использования в Управление параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов **текст** типа данных; Однако такое сравнение завершится ошибкой в случае с типами больших двоичных ОБЪЕКТОВ, где размер данных превышает 8 КБ.  
  
-   Специальные знаки в **ntext** данных может вызвать проблемы с SQLXML 4.0 из-за ограничений, налагаемых на сравнение типов больших двоичных ОБЪЕКТОВ. Например, использование «[Serializable]» в  **\<diffgr: перед >** блоков DiffGram при проверке столбца параллелизма **ntext** типа будут завершаться следующей SQLOLEDB Описание ошибки:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
