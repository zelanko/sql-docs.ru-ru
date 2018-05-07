---
title: Строка состояния | Документы Microsoft
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba4f36ad63ee5e7d9fada29d444e8cc36eca1bcf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="row-status"></a>Строки состояния
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров создается буфер в кэше для строки состояния. Библиотека курсоров извлекает значения для массива состояния строки (указанный атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR) из этого буфера. Для каждой строки библиотеку курсоров наборов этот буфер.  
  
-   SQL_ROW_DELETED при выполнении позиционированного удалить оператором в строке.  
  
-   SQL_ROW_ERROR при обнаружении ошибки при получении строки из источника данных с **SQLFetch**.  
  
-   SQL_ROW_SUCCESS при успешно извлекает строки из источника данных с **SQLFetch**.  
  
-   SQL_ROW_UPDATED при выполнении инструкции позиционированного обновления в строке.
