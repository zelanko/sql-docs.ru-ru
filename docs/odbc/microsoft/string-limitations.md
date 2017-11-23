---
title: "Строка ограничения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 260a530210b2e336067f2036f632cf347c1654f9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="string-limitations"></a>Строка ограничения
Максимальная длина строки инструкции SQL составляет 65 000 символов.  
  
 Когда используется драйвер Microsoft Access, поддерживаются только SQL-92 строковым константам (одинарные кавычки, не двойные кавычки).  
  
 Знак вертикальной черты (&#124;) не может использоваться в строке ли символ заключен в кавычки назад или нет.  
  
 Для максимальной совместимости приложений следует передавать параметры строки вместо передачи строки в кавычках.
