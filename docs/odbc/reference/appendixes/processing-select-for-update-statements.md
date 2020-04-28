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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 904028cd7b3798fcac8f9e5afa6186fae3e9fa29
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81308015"
---
# <a name="processing-select-for-update-statements"></a>Обработка инструкций SELECT FOR UPDATE
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Для обеспечения максимальной совместимости приложения должны формировать результирующие наборы, которые будут обновлены с помощью инструкции позиционированного обновления, выполняя инструкцию **SELECT для Update** . Хотя библиотека курсоров не требует этого, она необходима большинству источников данных, поддерживающих позиционированные инструкции UPDATE.  
  
 Библиотека курсоров пропускает столбцы в предложении **for Update** инструкции **SELECT FOR UPDATE** . Он удаляет это предложение перед передачей инструкции драйверу. В библиотеке курсоров атрибут SQL_ATTR_CONCURRENCYной инструкции вместе с ограничениями, упомянутыми в предыдущем разделе, определяет, можно ли обновить столбцы в результирующем наборе.
