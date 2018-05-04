---
title: По умолчанию запись о драйвере | Документы Microsoft
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
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c527f50ad8e71879a91b9b8f13262c5dce1a893f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="default-driver-subkey"></a>По умолчанию запись о драйвере
По умолчанию подраздел содержит одно значение, которое описывает драйвер, используемый источником данных по умолчанию. В следующей таблице показан формат данного значения.  
  
|Название|Тип данных|Данные |  
|----------|---------------|----------|  
|**Драйвер**|REG_SZ|*Описание для драйвера по умолчанию*|  
  
 *Описание по умолчанию драйвер* имя совпадает имя значения в подразделе драйверы ODBC, описывающий драйвер.  
  
 Например если источник данных по умолчанию использует драйвер SQL Server, может быть значение в подразделе по умолчанию.  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  По умолчанию драйвер, содержащийся в подразделе по умолчанию могут ссылаться на DSN пользователя по умолчанию или DSN системы по умолчанию. DSN пользователя по умолчанию и система по умолчанию созданы DSN, драйвер по умолчанию определяется DSN, который был создан и, наконец, поэтому может быть допустимым значением для источника данных, которая была создана первой.
