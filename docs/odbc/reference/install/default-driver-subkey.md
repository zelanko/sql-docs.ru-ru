---
title: По умолчанию запись о драйвере | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 6563627087ce8516f74f478b35f0f6a896aa025b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915739"
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
