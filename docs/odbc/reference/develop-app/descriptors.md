---
title: "Дескрипторы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f9a2016a57c9c2b9d105761c65be14809fee8798
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="descriptors"></a>Дескрипторы
Дескриптора ссылается на структуру данных, которая содержит информацию о столбцах или динамических параметров.  
  
 Функции ODBC, работать с данными столбцов и параметров, неявно задание и получение поля дескриптора. Например, если **SQLBindCol** вызывается привязка столбцов данных, он задает поля дескриптора, полностью описать привязки. Когда **SQLColAttribute** вызывается для описания столбцов данных, он возвращает данные, хранящиеся в поля дескриптора.  
  
 Вызов функций ODBC приложение требуется не связан с дескрипторами. Ни одна из операций базы данных необходимо, чтобы приложение обеспечивает прямой доступ к дескрипторам. Однако для некоторых приложений получения прямого доступа к дескрипторам упрощает многих операций. Например, прямой доступ к дескрипторам позволяет привязать данные столбцов, которые могут быть более эффективными, чем вызов **SQLBindCol** еще раз.  
  
> [!NOTE]  
>  Физическое представление дескриптора не определен. Приложениям получать непосредственный доступ к дескриптор только управляя ее полей путем вызова функции ODBC с помощью дескриптора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы дескрипторов](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Выделение и освобождение дескрипторов](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Получение и установка полей дескриптора](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
