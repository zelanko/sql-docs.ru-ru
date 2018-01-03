---
title: "Обработка инструкций SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 754630b1c125f416c52645510969c1165d8567ae
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="processing-sql-statements"></a>Обработка инструкций SQL
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров ODBC передает все инструкции SQL непосредственно к драйверу, за исключением следующих:  
  
-   Располагается update и delete  
  
-   **ВЫБЕРИТЕ для обновления** инструкций  
  
-   Пакетные инструкции SQL  
  
 Для выполнения позиционированное обновление и удаление операторов и поместите курсор на строку, чтобы вызвать **SQLGetData** для этой строки библиотеку курсоров создает инструкция по найденному, определяющее строку.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обработка инструкций позиционированного обновления и удаления](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Обработка инструкций SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Обработка пакетов инструкций SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Построение поисковых выражений](../../../odbc/reference/appendixes/constructing-searched-statements.md)
