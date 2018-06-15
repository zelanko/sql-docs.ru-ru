---
title: ResyncEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 3b974d00ecb1fb4d0d9d7e431f28df16f945d778
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281363"
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
