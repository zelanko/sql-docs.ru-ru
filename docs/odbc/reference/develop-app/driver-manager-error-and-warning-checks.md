---
title: Ошибка менеджера драйвера и проверки предупреждения (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee8a0f5ebfac8b6f87281806f07989f4980eb9b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305788"
---
# <a name="driver-manager-error-and-warning-checks"></a>Проверка ошибок и предупреждений диспетчера драйверов
Менеджер драйвера полностью или частично реализует ряд функций и, следовательно, проверяет все или некоторые ошибки и предупреждения в этих функциях.  
  
-   Менеджер драйверов реализует **S'LDataSources** и **S'LDrivers** и проверяет все ошибки и предупреждения в этих функциях.  
  
-   Менеджер драйвера проверяет, реализует ли драйвер **S'LGetFunctions.** Если драйвер не реализует **S'LGetFunctions,** менеджер драйвера реализует и проверяет все ошибки и предупреждения в нем.  
  
-   Менеджер драйверов частично реализует **s'LAllocHandle,** **S'LConnect**, **S'LDriverConnect,** **S'LBrowseConnect**, **S'LFreeHandle,** **S'LGetDiagRec,** а также **S'LGetDiagField** и проверяет некоторые ошибки в этих функциях. Он может вернуть те же ошибки, что и драйвер для некоторых из этих функций, поскольку оба выполняют аналогичные операции. Например, менеджер или драйвер драйвера может вернуть S'LSTATE IM008 (Dialog не удалось), если один из них не может отобразить окно диалога для **S'LDriverConnect.**
