---
title: "UPDATE, DELETE и INSERT инструкции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 592d135ccf66f8a9fde2cc064a51dc25617cf127
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="update-delete-and-insert-statements"></a>UPDATE, DELETE и инструкций INSERT
Приложения на основе SQL внесения изменений в таблицы, выполнив **обновление**, **удаление**, и **вставить** инструкции. Эти инструкции являются частью уровень соответствия грамматики минимальную SQL и должны поддерживаться все драйверы и источники данных.  
  
 Используется синтаксис этих операторов:  
  
 **ОБНОВЛЕНИЕ***имя таблицы*   
  
 **ЗАДАТЬ** *идентификатор столбца*  **=**  {*выражение* &#124; **NULL**}  
  
 [**,** *идентификатор столбца*  **=**  {*выражение* &#124; **NULL**}]...  
  
 [**ГДЕ** *условие поиска*]  
  
 **УДАЛИТЬ из** *имя таблицы*[**ГДЕ** *условие поиска*]  
  
 **INSERT INTO** *имя таблицы*[**(*** идентификатор столбца* [**,** *идентификатор столбца*]... **)**]  
  
 {*спецификация запроса* &#124;  **Значения (*** вставки значение* [**,** *вставки значение*]... **)**}  
  
 Обратите внимание, что *спецификация запроса* элемент действителен только в основные и расширенные SQL грамматики и что *выражение* и *условие поиска* элементы становятся более сложные в основные и расширенные SQL грамматики.  
  
 Как и другие инструкции SQL **обновления**, **удалить**, и **вставить** операторов, обычно более эффективно, если они используют параметры. Например следующая инструкция можно подготовить и многократно выполняется, чтобы вставить несколько строк в таблице Orders:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Такая эффективность можно увеличить путем передачи массивов, значений параметров. Дополнительные сведения о параметрах инструкции и массивы значений параметров см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
