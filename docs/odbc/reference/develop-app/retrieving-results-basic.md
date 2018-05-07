---
title: Извлечение результатов (Basic) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b09820c0716d6d7a8261ede3b5a4173dc73f384d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-results-basic"></a>Извлечение результатов (Basic)
Объект *результирующего набора* — это набор строк в источнике данных, отвечающих определенным условиям. Это основные таблицы, полученный в результате запроса и доступна для приложения в табличной форме. **ВЫБЕРИТЕ** операторы, функции работы с каталогами и некоторые процедуры создания результирующих наборов. В следующем примере первая инструкция SQL создает результирующий набор, содержащий все строки, а также все столбцы в таблице Orders, а вторая инструкция SQL создает результирующий набор, содержащий столбцы OrderID, менеджер по продажам и состояние для строк в таблице Orders в котором находится в состоянии ОТКРЫТЬ:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Результирующий набор может быть пустым, который отличается от результирующий набор вообще не. Например следующая инструкция SQL создает пустой результирующий набор:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Пустой результирующий набор ничем не отличается от какой-либо результат, установить, но не содержит строк. Например приложение можно получить метаданные для результирующего набора, можно при попытке выборки строки и необходимо закрыть курсор над результирующего набора.  
  
 Процесс извлечения строк из источника данных и их возврата в приложение называется *выборка*. В этом разделе описывается основные части этого процесса. Сведения о более сложных вещах, например блок и Прокручиваемые курсоры разделе [блочные курсоры](../../../odbc/reference/develop-app/block-cursors.md) и [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md). Сведения об обновлении, удаление и вставка строк, в разделе [Обзор обновления данных](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Был ли создан результирующий набор?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Метаданные результирующего набора](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Привязка столбцов](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Выборка данных](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md)
