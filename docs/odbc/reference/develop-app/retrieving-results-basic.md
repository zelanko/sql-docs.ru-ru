---
title: Извлечение результатов (базовые) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 8eb98d7c17663894e1bacdc27e431d6a54f45d3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772212"
---
# <a name="retrieving-results-basic"></a>Извлечение результатов (базовые возможности)
Объект *сам себя результирующий набор* представляет собой набор строк в источнике данных, который соответствует определенным условиям. Это основные таблицы, полученный в результате запроса и доступна для приложения в табличной форме. **ВЫБЕРИТЕ** операторы, функции работы с каталогами и некоторые процедуры создания результирующих наборов. В следующем примере первая инструкция SQL создает результирующий набор, содержащий все строки, а также все столбцы в таблице Orders, а вторая инструкция SQL создает результирующий набор, содержащий столбцы OrderID, менеджеров по продажам и состояние для строк в таблице Orders в котором открыт:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Результирующий набор может быть пустым, который отличается от результирующий набор вообще не. Например следующая инструкция SQL создает пустой результирующий набор:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Пустой результирующий набор ничем не отличается от любой другой результат, установить, но не содержит строк. К примеру приложение позволяет извлекать метаданные для результирующего набора, можно попытаться извлечь строки и необходимо закрыть курсор над результирующего набора.  
  
 Процесс извлечения строк из источника данных и их возврата в приложение называется *выборка*. Здесь объясняются основные части этого процесса. Узнать о более сложных вопросов, таких как блок и Прокручиваемые курсоры [блочные курсоры](../../../odbc/reference/develop-app/block-cursors.md) и [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md). Сведения об обновлении, удаление и вставка строк, см. в разделе [Обзор обновления данных](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Был ли создан результирующий набор?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Метаданные результирующего набора](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Привязка столбцов](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Выборка данных](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md)
