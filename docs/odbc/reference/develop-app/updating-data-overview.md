---
title: Общие сведения о данных обновление | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3edbd41bc5361d864abcc7d631a90521af98ef01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777833"
---
# <a name="updating-data-overview"></a>Общие сведения об обновлении данных
Приложения можно обновить данные, либо при выполнении инструкций SQL, либо путем вызова **SQLSetPos** или **SQLBulkOperations**. **ОБНОВЛЕНИЕ**, **удалить**, и **вставить** инструкций выступать непосредственно в источнике данных и обычно поддерживаются драйверы. Поиск обновления и инструкций delete содержит спецификацию для изменения строк. Расположенный update и delete и **SQLSetPos** работать на источник данных с помощью курсора и поддерживаются не часто.  
  
 Ли курсоров может обнаруживать изменения, внесенные в результирующий набор с помощью методов, описанных в этом разделе зависит от типа курсора и его реализации. Однопроходные курсоры не пересмотреть строк и поэтому не обнаружить все изменения. Сведения о ли Прокручиваемые курсоры может обнаруживать изменения, см. в разделе [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции UPDATE, DELETE и INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Инструкции позиционированного обновления и удаления](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Моделирование инструкций позиционированного обновления и удаления](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Определение числа затрагиваемых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Обновление данных с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Данные типа Long Data и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
