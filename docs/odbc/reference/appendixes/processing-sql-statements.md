---
title: "Обработка инструкций SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3613775e14453c2ed14e70cf122bd527217b2cd7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
-   [Обработка располагается инструкции Update и Delete](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Обработка SELECT для инструкции UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Обработки пакетов инструкций SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Создав поиск инструкций](../../../odbc/reference/appendixes/constructing-searched-statements.md)

