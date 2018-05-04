---
title: Имена таблиц | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1b1032ccda48d5a645e9992e2c501c851f51b7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
