---
title: Проверка согласованности | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2711f7d45ba433d97c36adb83b8400c6a386eac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="consistency-check"></a>Проверка согласованности
Проверка согласованности выполняется драйвер автоматически каждый раз, когда приложение задает поле SQL_DESC_DATA_PTR в APD, Отменить или IPD. Каждый раз, когда это поле имеет значение, драйвер проверяет значение поля SQL_DESC_TYPE и значения, применяемые к поле SQL_DESC_TYPE в той же записи, правильны и согласуются.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не задано; Однако приложение можно сделать, чтобы принудительно выполнить проверку согласованности IPD полей. Значение, равное поле SQL_DESC_DATA_PTR IPD фактически не сохраняются и не удается получить с помощью вызова **SQLGetDescField** или **SQLGetDescRec**; задание осуществляется только для принудительного Проверка согласованности. Невозможно выполнить проверку согласованности на IRD.  
  
 Дополнительные сведения о проверки согласованности см. в разделе [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
