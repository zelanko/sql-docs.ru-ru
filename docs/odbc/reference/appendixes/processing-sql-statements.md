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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d5aa94062f90154126fb18c3658adb39bb1d5c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057056"
---
# <a name="processing-sql-statements"></a>Обработка инструкций SQL
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Библиотека курсоров ODBC передает все инструкции SQL непосредственно к драйверу, за исключением следующих:  
  
-   Расположенный update и delete  
  
-   **SELECT FOR UPDATE** инструкций  
  
-   Пакетные инструкции SQL  
  
 Для выполнения позиционированного обновления и удаления и поместите курсор в строку для вызова **SQLGetData** для этой строки библиотеку курсоров создает инструкция по найденному, которая определяет строку.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обработка инструкций позиционированного обновления и удаления](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Обработка инструкций SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Обработка пакетов инструкций SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Построение поисковых выражений](../../../odbc/reference/appendixes/constructing-searched-statements.md)
