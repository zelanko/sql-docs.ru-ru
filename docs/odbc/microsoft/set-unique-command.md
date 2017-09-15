---
title: "Команда УНИКАЛЬНЫЙ НАБОР | Документы Microsoft"
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
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bed7fb14102c754d16409259fe7e1f5177652d05
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="set-unique-command"></a>УНИКАЛЬНЫЙ команды SET
Указывает, хранятся ли записи с повторяющимися значениями ключей в файле индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Указывает, не включены все записи со значением ключа индекса повторяющиеся в файле индекса. В файле индекса включается первой записи с исходное значение ключа индекса.  
  
 OFF  
 (По умолчанию). Указывает, что записи с повторяющимися значениями ключей будут включены в файл индекса.  
  
## <a name="remarks"></a>Замечания  
 Индексный файл сохраняет его ЗАДАТЬ УНИКАЛЬНЫЙ параметр выполните повторную ИНДЕКСАЦИЮ. Дополнительные сведения см. в разделе [ИНДЕКСА](../../odbc/microsoft/index-command.md).
