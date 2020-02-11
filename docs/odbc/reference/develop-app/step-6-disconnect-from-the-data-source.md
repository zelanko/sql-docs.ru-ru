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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114122"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Шаг 6. Отключение от источника данных
Последним шагом является отключение от источника данных, как показано на следующем рисунке. Во первых, приложение освобождает все дескрипторы операторов путем вызова **SQLFreeHandle**. Дополнительные сведения см. [в разделе освобождение маркера инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Отключение от источника данных](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Затем приложение отключается от источника данных с помощью **SQLDisconnect** и освобождает маркер подключения с помощью **SQLFreeHandle**. Дополнительные сведения см. в разделе [Отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Наконец, приложение освобождает обработчик среды с помощью **SQLFreeHandle** и выгружает диспетчер драйверов. Дополнительные сведения см. [в разделе Выделение маркера среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
