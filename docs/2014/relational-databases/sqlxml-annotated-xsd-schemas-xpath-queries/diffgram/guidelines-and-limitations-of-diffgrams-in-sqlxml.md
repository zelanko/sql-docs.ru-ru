---
title: Рекомендации и ограничения дельтами в SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1113bf11fcb3b1be2164bc6e685e6454323f3df
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013062"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Рекомендации и действующие ограничения SQLXML, связанные с дельтами
  При использовании дельт с SQLXML 4.0 учитывайте следующее.  
  
-   Типы больших двоичных объектов (BLOB), например `text/ntext` и изображения, не следует использовать в блоке `<diffgr:before>` при работе с дельтами, поскольку в этом случае они будут включены в управление параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов типа данных `text`; однако, в случае с типами больших двоичных объектов, когда размер данных превышает 8 КБ, такое сравнение завершится ошибкой.  
  
-   Специальные символы в данных типа `ntext` могут вызывать проблемы в работе SQLXML 4.0 из-за ограничений, налагаемых на сравнение типов больших двоичных объектов. Например, использование «[Serializable]» в блоке `<diffgr:before>` DiffGram при проверке параллелизма столбца с типом `ntext` завершится ошибкой со следующим описанием ошибки SQLOLEDB:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
