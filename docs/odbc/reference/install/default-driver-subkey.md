---
title: "По умолчанию запись о драйвере | Документы Microsoft"
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
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5c269705f5e4c0c855b5b7f929b1a76ee9523bd7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

