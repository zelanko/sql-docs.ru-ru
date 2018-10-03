---
title: Рекомендации и действующие ограничения SQLXML с Дельтами | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2adbd116b818086e13adacd5e88d3923b53f81ee
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074980"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Рекомендации и действующие ограничения SQLXML, связанные с дельтами
  При использовании дельт с SQLXML 4.0 учитывайте следующее.  
  
-   Типы больших двоичных объектов (BLOB), например `text/ntext` и изображения, не следует использовать в блоке `<diffgr:before>` при работе с дельтами, поскольку в этом случае они будут включены в управление параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов типа данных `text`; однако, в случае с типами больших двоичных объектов, когда размер данных превышает 8 КБ, такое сравнение завершится ошибкой.  
  
-   Специальные символы в данных типа `ntext` могут вызывать проблемы в работе SQLXML 4.0 из-за ограничений, налагаемых на сравнение типов больших двоичных объектов. Например, использование «[Serializable]» в блоке `<diffgr:before>` DiffGram при проверке параллелизма столбца с типом `ntext` завершится ошибкой со следующим описанием ошибки SQLOLEDB:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
