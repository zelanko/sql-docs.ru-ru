---
title: Шаг 2. Инициализировать приложение | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0d25173dc8dc14aa1ed41a4a88496ef654e2ff0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149194"
---
# <a name="step-2-initialize-the-application"></a>Шаг 2. Инициализация приложения
Второй шаг — для инициализации этого приложения, как показано на следующем рисунке. Именно здесь выполняемые операции зависит от приложения.  
  
 ![Показывает, инициализация ODBC приложения](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 На этом этапе обычно используется **SQLGetInfo** раскрывать возможности драйвера. Дополнительные сведения см. в разделе [рассмотрении функции базы данных для использования](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Все приложения должны выделить дескриптор инструкции с **SQLAllocHandle**, и задайте атрибуты инструкции, такие как тип курсора, во многих приложениях **SQLSetStmtAttr**. Дополнительные сведения см. в разделе [выделить дескриптор инструкции](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) и [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).
