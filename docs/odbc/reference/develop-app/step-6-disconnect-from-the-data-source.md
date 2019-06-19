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
manager: craigg
ms.openlocfilehash: a42465e763f8f6d520ed9c1dac42612aa1b28575
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149220"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Шаг 6. Отключение от источника данных
Последним шагом является отключение от источника данных, как показано на следующем рисунке. Во-первых, приложение освободит все дескрипторы инструкций путем вызова **SQLFreeHandle**. Дополнительные сведения см. в разделе [освободить дескриптор инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Показывает, отключение от источника данных](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Затем приложение отключается от источника данных с помощью **SQLDisconnect** и освобождает дескриптор соединения с **SQLFreeHandle**. Дополнительные сведения см. в разделе [отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Наконец, приложение освобождает дескриптор среды с **SQLFreeHandle** и выгружает диспетчера драйверов. Дополнительные сведения см. в разделе [выделение маркер среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
