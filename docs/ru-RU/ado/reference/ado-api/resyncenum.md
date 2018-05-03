---
title: ResyncEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c755c31e055429c220742f35cef5f49ba8459870
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="resyncenum"></a>ResyncEnum
Указывает, перезаписываются ли базовые значения путем вызова [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|По умолчанию. Данные будут утеряны и отложенные обновления будут отменены.|  
|**adResyncUnderlyingValues**|1|Не приводит к перезаписи данных и отложенные обновления не будут отменены.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Resync](../../../ado/reference/ado-api/resync-method.md)
