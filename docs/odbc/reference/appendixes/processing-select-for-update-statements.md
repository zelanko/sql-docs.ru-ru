---
title: Обработка инструкций SELECT FOR UPDATE | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 7f54d31426773f294a4a23f059c9f906d430056f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057032"
---
# <a name="processing-select-for-update-statements"></a>Обработка инструкций SELECT FOR UPDATE
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Для максимальной совместимости приложений должна создавать результирующие наборы, которые будут обновлены с помощью инструкции позиционированного обновления, выполнив **ВЫБЕРИТЕ для обновления** инструкции. Несмотря на то, что библиотека курсоров нет такого требования, он необходим для большинства источников данных, которые поддерживают инструкций позиционированного обновления.  
  
 Библиотека курсоров не учитывает столбцы в **FOR UPDATE** предложении **SELECT FOR UPDATE** оператор; оно удаляет это предложение перед передачей инструкция драйвер. В библиотеку курсоров атрибута инструкции SQL_ATTR_CONCURRENCY, а также ограничения, описанные в предыдущем разделе, элементов управления столбцов в результирующем наборе могут ли быть обновлены.
