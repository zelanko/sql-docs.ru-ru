---
title: "Строка ограничения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e6f9d8add08f80b59adaa42f02bc1da006356081
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="string-limitations"></a>Строка ограничения
Максимальная длина строки инструкции SQL составляет 65 000 символов.  
  
 Когда используется драйвер Microsoft Access, поддерживаются только SQL-92 строковым константам (одинарные кавычки, не двойные кавычки).  
  
 Знак вертикальной черты (&#124;) не может использоваться в строке ли символ заключен в кавычки назад или нет.  
  
 Для максимальной совместимости приложений следует передавать параметры строки вместо передачи строки в кавычках.
