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
ms.openlocfilehash: 41030015645bda11242a703a163f26104e66dba0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114248"
---
# <a name="step-2-initialize-the-application"></a>Шаг 2. Инициализация приложения
Второй шаг — для инициализации этого приложения, как показано на следующем рисунке. Именно здесь выполняемые операции зависит от приложения.  
  
 ![Показывает, инициализация ODBC приложения](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 На этом этапе обычно используется **SQLGetInfo** раскрывать возможности драйвера. Дополнительные сведения см. в разделе [рассмотрении функции базы данных для использования](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Все приложения должны выделить дескриптор инструкции с **SQLAllocHandle**, и задайте атрибуты инструкции, такие как тип курсора, во многих приложениях **SQLSetStmtAttr**. Дополнительные сведения см. в разделе [выделить дескриптор инструкции](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) и [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).
