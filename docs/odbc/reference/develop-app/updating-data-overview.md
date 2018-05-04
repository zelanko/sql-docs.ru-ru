---
title: Обновление данных Обзор | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce36f2467ce4da80f726c0f9370180422edddf49
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-overview"></a>Обзор обновления данных
Приложения можно обновлять данные при выполнении инструкций SQL или вызвав **SQLSetPos** или **SQLBulkOperations**. **ОБНОВЛЕНИЕ**, **удаление**, и **вставить** инструкций работать непосредственно в источнике данных и обычно поддерживаются по драйверы. Поиск обновлений и инструкций delete содержит спецификацию строк для изменения. Располагается update и delete и **SQLSetPos** работать в источнике данных через курсор и не поддерживаются.  
  
 Ли курсоров может обнаружить изменения, внесенные в результирующий набор с помощью методов, описанных в этом разделе зависит от типа курсора и его реализации. Однопроходные курсоры не повторное использование строк и поэтому не обнаруживают все изменения. Сведения о выяснять Прокручиваемые курсоры изменения содержатся [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции UPDATE, DELETE и INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Инструкции позиционированного обновления и удаления](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Моделирование инструкций позиционированного обновления и удаления](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Определение числа затрагиваемых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Обновление данных с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Данные типа Long Data и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
