---
title: "Функции каталога | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 497676e6b87b6603d4bc6cb1615bb1b133c7acd4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions"></a>Функции работы с каталогами
Все базы данных имеют структуру, описывающий, каким образом данные будут храниться в базе данных. Например база данных простого заказа на продажу может иметь структуре показано на следующем рисунке, в котором используются столбцы идентификатор установить связь между таблицами.  
  
 ![Структура простой базы данных](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Эта структура вместе с другими сведениями, например правами, хранится в набор системных таблиц базы данных называется *каталога,* которого называется также *словарь данных*.  
  
 Приложение может обнаружить эту структуру через вызовы *функции каталога*. Функции каталога возвращают сведения в результирующих наборах и обычно реализуется с помощью **ВЫБЕРИТЕ** инструкции для таблиц в каталоге. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использует данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Функций каталога ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

