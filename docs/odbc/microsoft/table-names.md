---
title: "Имена таблиц | Документы Microsoft"
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
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 480ca31108b608139b5563f0c18d1fa020e76f75
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="table-names"></a>Имена таблиц
Если расширение имени dBASE, Microsoft Excel, Paradox, или текста, используемого драйвера, имена таблиц, которые происходят в предложении FROM SELECT или DELETE, после предложения INTO в инструкции INSERT и UPDATE, CREATE TABLE и DROP TABLE может содержать допустимый путь, имя первичного и файла .  
  
 Использование имени таблицы в любом месте инструкции SQL не поддерживает использование пути или расширения, но принимает только основное имя (например, EMP из C:\ABC\EMP).  
  
 Корреляционные имена (псевдонимы) может использоваться. Например:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```

