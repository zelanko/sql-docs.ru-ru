---
description: Общие сведения об обновлении данных
title: Общие сведения об обновлении данных | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b1755ea75426030a96ed7b349cc82f0fc7e282a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424426"
---
# <a name="updating-data-overview"></a>Общие сведения об обновлении данных
Приложения могут обновлять данные либо путем исполнения инструкций SQL, либо путем вызова **SQLSetPos** или **SQLBulkOperations**. Инструкции **Update**, **Delete**и **INSERT** действуют непосредственно в источнике данных и обычно поддерживаются драйверами. Поиск в инструкциях UPDATE и DELETE содержит спецификацию изменяемых строк. Позиционированные инструкции UPDATE и DELETE и **SQLSetPos** действуют в источнике данных с помощью курсора и менее широко поддерживаются.  
  
 Могут ли курсоры обнаруживать изменения, внесенные в результирующий набор с помощью методов, описанных в этом разделе, зависит от типа курсора и его реализации. Однонаправленные курсоры не пересматривают строки и, следовательно, не обнаруживают изменения. Сведения о том, могут ли прокручиваемые курсоры обнаруживать изменения, см. в разделе [прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции UPDATE, DELETE и INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Инструкции позиционированного обновления и удаления](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Моделирование инструкций позиционированного обновления и удаления](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Определение числа затрагиваемых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Обновление данных с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Данные типа Long Data и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
