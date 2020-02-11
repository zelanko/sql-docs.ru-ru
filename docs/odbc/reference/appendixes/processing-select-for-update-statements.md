---
title: Обработка инструкции SELECT для инструкций UPDATE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ad9a20ab8abd40123ec4e4d7369373e68699205
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028362"
---
# <a name="processing-select-for-update-statements"></a>Обработка инструкций SELECT FOR UPDATE
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Для обеспечения максимальной совместимости приложения должны формировать результирующие наборы, которые будут обновлены с помощью инструкции позиционированного обновления, выполняя инструкцию **SELECT для Update** . Хотя библиотека курсоров не требует этого, она необходима большинству источников данных, поддерживающих позиционированные инструкции UPDATE.  
  
 Библиотека курсоров пропускает столбцы в предложении **for Update** инструкции **SELECT FOR UPDATE** . Он удаляет это предложение перед передачей инструкции драйверу. В библиотеке курсоров атрибут SQL_ATTR_CONCURRENCYной инструкции вместе с ограничениями, упомянутыми в предыдущем разделе, определяет, можно ли обновить столбцы в результирующем наборе.
