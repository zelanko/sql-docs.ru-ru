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
ms.topic: conceptual
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f707c99b626b27bd35de011e8d1eb78d801e614
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="implementation-notes"></a>Примечания по реализации
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе описывается реализация библиотеки курсоров ODBC. Здесь описывается, как библиотека курсоров сохраняет свой кэш, выполняет инструкции SQL и реализует функции ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Кэш библиотеки курсоров](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [Обработка инструкций SQL](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [Функции ODBC и библиотека курсоров](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
