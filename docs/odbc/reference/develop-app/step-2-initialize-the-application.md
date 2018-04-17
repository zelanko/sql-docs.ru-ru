---
title: 'Шаг 2: Инициализируйте приложение | Документы Microsoft'
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
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf8cf5a5d697b1e8c52da84d93ccf23c6e127c3b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="step-2-initialize-the-application"></a>Шаг 2: Инициализации приложения
Второй шаг — для инициализации приложения, как показано на следующем рисунке. Именно здесь выполняемые операции зависит от приложения.  
  
 ![Показывает, инициализация ODBC приложения](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 На этом этапе обычно используется **SQLGetInfo** для обнаружения возможностей драйвера. Дополнительные сведения см. в разделе [рассмотрении функции базы данных для использования](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Все приложения должны выделить дескриптор инструкции с **SQLAllocHandle**, и задайте атрибуты инструкции, такие как тип курсора, во многих приложениях **SQLSetStmtAttr**. Дополнительные сведения см. в разделе [выделения дескриптор инструкции](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) и [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).
