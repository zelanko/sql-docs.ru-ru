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
ms.openlocfilehash: e82644d3bddab5d4f6fde6f7103bd9731872bab9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094190"
---
# <a name="default-driver-subkey"></a>Подраздел драйвера по умолчанию
По умолчанию подраздел содержит одно значение, которое описывает драйвер, используемый источник данных по умолчанию. В следующей таблице показан формат данного значения.  
  
|Name|Тип данных|Data|  
|----------|---------------|----------|  
|**Драйвер**|REG_SZ|*Описание по умолчанию драйвер*|  
  
 *Описание по умолчанию драйвер* — это имя совпадает с именем значения в подразделе драйверы ODBC, который описывает драйвер.  
  
 Например если источник данных по умолчанию использует драйвер SQL Server, может быть значение подраздела по умолчанию:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  По умолчанию драйвер, содержатся в подразделе по умолчанию могут ссылаться на DSN пользователя по умолчанию или DSN системы по умолчанию. Если DSN пользователя по умолчанию и система по умолчанию имя источника данных будут созданы, по умолчанию драйвер определяется DSN, который был создан последним, так что он может не является допустимым значением для источника данных, который сначала был создан.
