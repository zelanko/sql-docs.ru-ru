---
title: 'Шаг 6: Отключение от источника данных (ru) Документы Майкрософт'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df8cd94435d74bf813b0b64be0753a0beb44d354
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302795"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Шаг 6. Отключение от источника данных
Последним шагом является отключение от источника данных, как показано на следующей иллюстрации. Во-первых, приложение освобождает любые ручки оператора, позвонив по **s'LFreeHandle.** Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)  
  
 ![Отключение от источника данных](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Далее приложение отключается от исходного кода данных с **помощью S'LDisconnect** и освобождает ручку соединения с **помощью S'LFreeHandle.** Для получения дополнительной [информации](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)см.  
  
 Наконец, приложение освобождает обработку среды с **помощью S'LFreeHandle** и выгружает менеджера драйвера. Для получения дополнительной [Allocating the Environment Handle](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)информации см.
