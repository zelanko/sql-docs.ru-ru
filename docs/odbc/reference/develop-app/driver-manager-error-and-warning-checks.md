---
title: Диспетчер драйверов ошибки и предупреждения проверки | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20b411544e4d4ac54dc32cdbd126868f313b75c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="driver-manager-error-and-warning-checks"></a>Диспетчер драйверов ошибки и предупреждения проверки
Диспетчер драйверов полностью или частично реализует ряд функций и проверяет, поэтому для всех или некоторых ошибок и предупреждений в этих функциях.  
  
-   Диспетчер драйверов реализует **SQLDataSources** и **SQLDrivers** и проверяет все ошибки и предупреждения в эти функции.  
  
-   Диспетчер драйверов проверяет, реализует ли драйвер **SQLGetFunctions**. Если драйвер не реализует **SQLGetFunctions**, диспетчер драйверов реализует и проверяет все ошибки и предупреждения в нем.  
  
-   Диспетчер драйверов частично реализует **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**,  **SQLFreeHandle**, **SQLGetDiagRec**, и **SQLGetDiagField** и проверяет некоторые ошибки в этих функций. Так как оба выполняют аналогичные операции может вернуть те же ошибки, как драйвер для некоторых из этих функций. Например, диспетчер драйверов или драйвер может возвращать SQLSTATE IM008 (Сбой диалогового окна) при вызове одной не удалось отобразить диалоговое окно входа для **SQLDriverConnect**.
