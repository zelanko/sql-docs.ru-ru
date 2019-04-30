---
title: Подраздел драйвера по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d78101fd564e18467e6833f480cec2409dc2c44b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198306"
---
# <a name="default-driver-subkey"></a>Подраздел драйвера по умолчанию
По умолчанию подраздел содержит одно значение, которое описывает драйвер, используемый источник данных по умолчанию. В следующей таблице показан формат данного значения.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|**Драйвер**|REG_SZ|*Описание по умолчанию драйвер*|  
  
 *Описание по умолчанию драйвер* — это имя совпадает с именем значения в подразделе драйверы ODBC, который описывает драйвер.  
  
 Например если источник данных по умолчанию использует драйвер SQL Server, может быть значение подраздела по умолчанию:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  По умолчанию драйвер, содержатся в подразделе по умолчанию могут ссылаться на DSN пользователя по умолчанию или DSN системы по умолчанию. Если DSN пользователя по умолчанию и система по умолчанию имя источника данных будут созданы, по умолчанию драйвер определяется DSN, который был создан последним, так что он может не является допустимым значением для источника данных, который сначала был создан.
