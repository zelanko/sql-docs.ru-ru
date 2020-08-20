---
description: Подраздел драйвера по умолчанию
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d78cc54253d002c54510fdc47f46f10de9281b65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494557"
---
# <a name="default-driver-subkey"></a>Подраздел драйвера по умолчанию
Подраздел по умолчанию содержит единственное значение, описывающее драйвер, используемый источником данных по умолчанию. Формат этого значения показан в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|**Драйвер**|REG_SZ|*по умолчанию-Описание драйвера*|  
  
 Имя *драйвера-описания по умолчанию* совпадает с именем значения в подразделе драйверов ODBC, описывающем драйвер.  
  
 Например, если источник данных по умолчанию использует драйвер SQL Server, то значение в подразделе по умолчанию может быть следующим:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Драйвер по умолчанию, содержащийся в подразделе по умолчанию, может ссылаться либо на DSN пользователя по умолчанию, либо на системный DSN по умолчанию. Если были созданы как DSN пользователя по умолчанию, так и системное имя DSN по умолчанию, драйвер по умолчанию определяется именем DSN, которое было создано последним, поэтому оно может не быть допустимой записью для имени DSN, которое было создано первым.
