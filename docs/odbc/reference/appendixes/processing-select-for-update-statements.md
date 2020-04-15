---
title: Обработка SELECT ДЛЯ ОТЧЕТных Заявлений (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308015"
---
# <a name="processing-select-for-update-statements"></a>Обработка инструкций SELECT FOR UPDATE
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Для максимальной совместимости приложения должны генерировать наборы результатов, которые будут обновлены с позиционным заявлением об обновлении, выполнив заявление **SELECT FOR UPDATE.** Хотя библиотека курсоров не требует этого, она требуется большинством источников данных, поддерживающих позиционированные операторы обновления.  
  
 Библиотека курсора игнорирует столбцы в пункте **ДЛЯ ОБНОВЛЕНИЕ** заявления SELECT **FOR UPDATE;** он удаляет это положение перед передачей заявления водителю. В библиотеке курсоров, атрибут SQL_ATTR_CONCURRENCY оператора, наряду с ограничениями, упомянутыми в предыдущем разделе, контролирует, можно ли обновить столбцы в наборе результатов.
