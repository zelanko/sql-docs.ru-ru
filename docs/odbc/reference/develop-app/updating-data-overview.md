---
title: "Обновление данных Обзор | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3da35917f3979b041d6eb5b61d6554d4ef4c4585
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data-overview"></a>Обзор обновления данных
Приложения можно обновлять данные при выполнении инструкций SQL или вызвав **SQLSetPos** или **SQLBulkOperations**. **ОБНОВЛЕНИЕ**, **удаление**, и **вставить** инструкций работать непосредственно в источнике данных и обычно поддерживаются по драйверы. Поиск обновлений и инструкций delete содержит спецификацию строк для изменения. Располагается update и delete и **SQLSetPos** работать в источнике данных через курсор и не поддерживаются.  
  
 Ли курсоров может обнаружить изменения, внесенные в результирующий набор с помощью методов, описанных в этом разделе зависит от типа курсора и его реализации. Однопроходные курсоры не повторное использование строк и поэтому не обнаруживают все изменения. Сведения о выяснять Прокручиваемые курсоры изменения содержатся [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [UPDATE, DELETE и инструкций INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Позиционированное обновление и удаление операторов](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Имитация позиционированного обновления и инструкций Delete](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Определение числа затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Обновление данных с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Большие объемы данных и SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)

