---
title: "По умолчанию запись о драйвере | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6abe4c5b5b07ea59b18c1bd298225ca33db2a65b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="default-driver-subkey"></a>По умолчанию запись о драйвере
По умолчанию подраздел содержит одно значение, которое описывает драйвер, используемый источником данных по умолчанию. В следующей таблице показан формат данного значения.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|**Драйвер**|REG_SZ|*Описание для драйвера по умолчанию*|  
  
 *Описание по умолчанию драйвер* имя совпадает имя значения в подразделе драйверы ODBC, описывающий драйвер.  
  
 Например если источник данных по умолчанию использует драйвер SQL Server, может быть значение в подразделе по умолчанию.  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  По умолчанию драйвер, содержащийся в подразделе по умолчанию могут ссылаться на DSN пользователя по умолчанию или DSN системы по умолчанию. DSN пользователя по умолчанию и система по умолчанию созданы DSN, драйвер по умолчанию определяется DSN, который был создан и, наконец, поэтому может быть допустимым значением для источника данных, которая была создана первой.
