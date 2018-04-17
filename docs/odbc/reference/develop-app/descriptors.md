---
title: Дескрипторы | Документы Microsoft
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
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8362a8dd210579ebca0d303ca29661a3774ea4cd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
