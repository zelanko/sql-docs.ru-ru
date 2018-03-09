---
title: "Примечания по реализации | Документы Microsoft"
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
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 017c58b72d1b190d8d11f08cf7ecce5ff58f65b1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="implementation-notes"></a>Примечания по реализации
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе описывается реализация библиотеки курсоров ODBC. Здесь описывается, как библиотека курсоров сохраняет свой кэш, выполняет инструкции SQL и реализует функции ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Кэш библиотеки курсоров](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [Обработка инструкций SQL](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [Функции ODBC и библиотека курсоров](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
