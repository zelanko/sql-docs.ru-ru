---
title: Строка ограничения | Документы Microsoft
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
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a8e90ace4e237b7945da4a43ad869b79c657ab2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="string-limitations"></a>Строка ограничения
Максимальная длина строки инструкции SQL составляет 65 000 символов.  
  
 Когда используется драйвер Microsoft Access, поддерживаются только SQL-92 строковым константам (одинарные кавычки, не двойные кавычки).  
  
 Знак вертикальной черты (&#124;) не может использоваться в строке ли символ заключен в кавычки назад или нет.  
  
 Для максимальной совместимости приложений следует передавать параметры строки вместо передачи строки в кавычках.
