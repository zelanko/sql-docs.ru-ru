---
title: "Строка состояния | Документы Microsoft"
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f164b8269e1150cdf7a85e486bcc3fd93a9411f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="row-status"></a>Строки состояния
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров создается буфер в кэше для строки состояния. Библиотека курсоров извлекает значения для массива состояния строки (указанный атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR) из этого буфера. Для каждой строки библиотеку курсоров наборов этот буфер.  
  
-   SQL_ROW_DELETED при выполнении позиционированного удалить оператором в строке.  
  
-   SQL_ROW_ERROR при обнаружении ошибки при получении строки из источника данных с **SQLFetch**.  
  
-   SQL_ROW_SUCCESS при успешно извлекает строки из источника данных с **SQLFetch**.  
  
-   SQL_ROW_UPDATED при выполнении инструкции позиционированного обновления в строке.
