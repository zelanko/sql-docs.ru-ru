---
title: Получение результатов (базовый) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7abe4dd2f0bfb0b5302022d8e50cddc7df84f192
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020470"
---
# <a name="retrieving-results-basic"></a>Извлечение результатов (базовые возможности)
*Результирующий набор* — это набор строк в источнике данных, соответствующих определенным условиям. Это концептуальная таблица, полученная из запроса и доступная для приложения в табличной форме. Инструкции **SELECT** , функции каталогизации и некоторые процедуры создают результирующие наборы. В следующем примере первая инструкция SQL создает результирующий набор, содержащий все строки и все столбцы в таблице Orders, а вторая инструкция SQL создает результирующий набор, содержащий значения столбцов OrderID, SalesPerson и Status для строк в таблице Orders. в состоянии открыто:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Результирующий набор может быть пустым, что отличается от результирующего набора. Например, следующая инструкция SQL создает пустой результирующий набор:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Пустой результирующий набор не отличается от любого другого результирующего набора, за исключением того, что в нем нет строк. Например, приложение может получить метаданные для результирующего набора, может попытаться получить строки и закрыть курсор над результирующим набором.  
  
 Процесс получения строк из источника данных и их возврата в приложение называется *получением*. В этом разделе объясняются основные части этого процесса. Сведения о более сложных разделах, таких как блочные и прокручиваемые курсоры, см. в разделе [блочные курсоры](../../../odbc/reference/develop-app/block-cursors.md) и [прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md). Сведения об обновлении, удалении и вставке строк см. в разделе [Обновление данных обзор](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Был ли создан результирующий набор?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Метаданные результирующего набора](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Привязка столбцов](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Выборка данных](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md)
