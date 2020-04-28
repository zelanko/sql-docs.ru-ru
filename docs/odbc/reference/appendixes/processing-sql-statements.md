---
title: Обработка инструкций SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eda640f6e810eeccbfa17ea2b6ba7c1b19b28e08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81308005"
---
# <a name="processing-sql-statements"></a>Обработка инструкций SQL
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсоров ODBC передает все инструкции SQL непосредственно в драйвер, за исключением следующих:  
  
-   Инструкции позиционированного обновления и удаления  
  
-   **SELECT для инструкций UPDATE**  
  
-   Пакетные инструкции SQL  
  
 Для выполнения позиционированных инструкций UPDATE и DELETE и позиционирования курсора в строке для вызова **SQLGetData** для этой строки библиотека курсоров формирует поисковую инструкцию, идентифицирующую строку.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обработка инструкций позиционированного обновления и удаления](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Обработка инструкций SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Обработка пакетов инструкций SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Построение поисковых выражений](../../../odbc/reference/appendixes/constructing-searched-statements.md)
