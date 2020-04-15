---
title: Получение Результатов (Основные) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f7d01bf92fcee07940e449a2fb4bbac4f0fe6ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304335"
---
# <a name="retrieving-results-basic"></a>Извлечение результатов (базовые возможности)
Набор *результатов* представляет собой набор строк на источнике данных, который соответствует определенным критериям. Это концептуальная таблица, которая является результатом запроса и доступна для приложения в табликовой форме. **Заявления SELECT,** функции каталога и некоторые процедуры создают наборы результатов. В следующем примере в первом отчете S'L создается набор результатов, содержащий все строки и все столбцы в таблице заказов, а вторая выписка S'L создает набор результатов, содержащий столбцы OrderID, SalesPerson и Status для строк в таблице заказов, в которой статус OPEN:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Набор результатов может быть пустым, что отличается от того, что не установлено вообще. Например, в следующем заявлении S'L создается пустой набор результатов:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Пустой набор результатов ничем не отличается от любого другого набора результатов, за исключением того, что он не имеет строк. Например, приложение может получать метаданные для набора результатов, пытаться получить строки и закрывать курсор над набором результатов.  
  
 Процесс извлечения строк из источника данных и их возврата в приложение называется *извлечением.* В этом разделе разъясняются основные части этого процесса. Для получения информации о более продвинутых темах, таких как блок и [Scrollable Cursors](../../../odbc/reference/develop-app/scrollable-cursors.md)прокрутки курсоры, [см.](../../../odbc/reference/develop-app/block-cursors.md) Для получения информации об обновлении, удалии и вставке строк [см.](../../../odbc/reference/develop-app/updating-data-overview.md)  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Был ли создан результирующий набор?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Метаданные результирующего набора](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Привязка столбцов](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Выборка данных](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md)
