---
title: Примечания по реализации | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65facfed98692db0d8a9ce2e76e4973f8fbd9601
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="implementation-notes"></a>Примечания по реализации
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе описывается реализация библиотеки курсоров ODBC. Здесь описывается, как библиотека курсоров сохраняет свой кэш, выполняет инструкции SQL и реализует функции ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Кэш библиотеки курсоров](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [Обработка инструкций SQL](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [Функции ODBC и библиотека курсоров](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
