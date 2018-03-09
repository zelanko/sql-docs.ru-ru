---
title: "ResyncEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aecc0ca8d53aa4eb1986b55c178943a3acf752f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
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
