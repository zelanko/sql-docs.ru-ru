---
title: Подключка драйвера по умолчанию (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb134d670964e352d94c13474d8a72fa4bd494ba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301057"
---
# <a name="default-driver-subkey"></a>Подраздел драйвера по умолчанию
Подключка по умолчанию содержит одно значение, описывая драйвер, используемый источником данных по умолчанию. Формат этого значения отображается в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|**Драйвер**|REG_SZ|*по умолчанию драйвер-описание*|  
  
 Имя *драйвера-описания по умолчанию* совпадает с именем значения под подключкой ODBC Drivers, описывающая драйвер.  
  
 Например, если источник данных по умолчанию использует драйвер s'L Server, значение под подключкой по умолчанию может быть:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Драйвер по умолчанию, содержащийся в подключке по умолчанию, может относиться либо к пользователю DSN по умолчанию, либо к системе DSN по умолчанию. Если были созданы как пользователь DSN по умолчанию, так и система DSN по умолчанию, драйвер по умолчанию определяется DSN, который был создан последним, поэтому он может быть недействительным для DSN, который был создан первым.
