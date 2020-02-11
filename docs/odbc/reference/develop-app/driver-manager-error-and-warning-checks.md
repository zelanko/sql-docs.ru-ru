---
title: Проверка ошибок и предупреждений диспетчера драйверов | Документация Майкрософт
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
ms.openlocfilehash: 6d0b136b9748de1991888abb0c19bc0d2ac65ea0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046968"
---
# <a name="driver-manager-error-and-warning-checks"></a>Проверка ошибок и предупреждений диспетчера драйверов
Диспетчер драйверов полностью или частично реализует ряд функций и, следовательно, проверяет наличие всех ошибок и предупреждений в этих функциях.  
  
-   Диспетчер драйверов реализует **SQLDataSources** и **SQLDrivers** и проверяет все ошибки и предупреждения в этих функциях.  
  
-   Диспетчер драйверов проверяет, реализует ли драйвер **SQLGetFunctions**. Если драйвер не реализует **SQLGetFunctions**, диспетчер драйверов реализует и проверяет все ошибки и предупреждения в нем.  
  
-   Диспетчер драйверов частично реализует **функцию SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**, **SQLFreeHandle**, **SQLGetDiagRec**и **SQLGetDiagField** и проверяет наличие ошибок в этих функциях. Он может возвращать те же ошибки, что и драйвер для некоторых из этих функций, так как оба выполняют аналогичные операции. Например, диспетчер драйверов или драйвер может вернуть значение SQLSTATE IM008 (диалоговое окно не удалось), если ни один из них не может отобразить диалоговое окно входа для **SQLDriverConnect**.
