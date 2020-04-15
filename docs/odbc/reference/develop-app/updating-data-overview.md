---
title: Обновление обзорных данных (ru) Документы Майкрософт
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
ms.openlocfilehash: 9972ab61f041385ae4ca616df093ae63ad7a47d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300390"
---
# <a name="updating-data-overview"></a>Общие сведения об обновлении данных
Приложения могут обновлять данные либо путем выполнения заявлений s-L, либо потелефонистой **s'LSetPos** или **S'LBulkOperations.** **ОБНОВЛЕНИЕ**, **DELETE**, и **INSERT** заявления действуют непосредственно на источник данных и, как правило, поддерживаются драйверами. Поисковые инструкции по обновлению и удалению содержат спецификацию строк для изменения. Позиционированные операторы обновления и удаления, а **также S'LSetPos** действуют на источник данных через курсор и получают менее широкую поддержку.  
  
 Могут ли курсоры обнаружить изменения, внесенные в набор результатов с помощью методов, описанных в этом разделе, зависит от типа курсора и способа его реализации. Курсоры только для форварда не пересматривают строки и поэтому не обнаруживают никаких изменений. Для получения информации о том, могут ли прокрутки курсоры обнаружить изменения, [см.](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции UPDATE, DELETE и INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Инструкции позиционированного обновления и удаления](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Моделирование инструкций позиционированного обновления и удаления](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Определение числа затрагиваемых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Обновление данных с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Данные типа Long Data и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
