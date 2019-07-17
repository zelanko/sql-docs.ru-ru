---
title: Шаг 6. Отключение от источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65cc2ae8d2c2248a733e6efa9537fd3b40bb8fd1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114122"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Шаг 6. Отключение от источника данных
Последним шагом является отключение от источника данных, как показано на следующем рисунке. Во-первых, приложение освободит все дескрипторы инструкций путем вызова **SQLFreeHandle**. Дополнительные сведения см. в разделе [освободить дескриптор инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Показывает, отключение от источника данных](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Затем приложение отключается от источника данных с помощью **SQLDisconnect** и освобождает дескриптор соединения с **SQLFreeHandle**. Дополнительные сведения см. в разделе [отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Наконец, приложение освобождает дескриптор среды с **SQLFreeHandle** и выгружает диспетчера драйверов. Дополнительные сведения см. в разделе [выделение маркер среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
