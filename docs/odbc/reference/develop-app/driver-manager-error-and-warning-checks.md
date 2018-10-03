---
title: Проверка диспетчера драйверов ошибок и предупреждений | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e00b6907d58cda1708cf61907d3c5ff6bf56edfa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848982"
---
# <a name="driver-manager-error-and-warning-checks"></a>Проверка ошибок и предупреждений диспетчера драйверов
Диспетчер драйверов полностью или частично реализован ряд функций и поэтому проверяет все или некоторые ошибки и предупреждения в этих функциях.  
  
-   Диспетчер драйверов реализует **SQLDataSources** и **SQLDrivers** и проверяет все ошибки и предупреждения в этих функциях.  
  
-   Диспетчер драйверов проверяет, реализует ли драйвер **SQLGetFunctions**. Если драйвер не реализует **SQLGetFunctions**, the Driver Manager реализует и проверяет, все ошибки и предупреждения в нем.  
  
-   Диспетчер драйверов частично реализующий **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**,  **SQLFreeHandle**, **SQLGetDiagRec**, и **SQLGetDiagField** и проверяет наличие ошибки в этих функциях. Так как оба средства выполняют аналогичные операции может вернуть те же ошибки, как драйвер для некоторых из этих функций. Например, диспетчер драйверов или драйвер может возвращать SQLSTATE IM008 (ошибка диалогового окна) если он не удалось отобразить диалоговое окно входа для **SQLDriverConnect**.
