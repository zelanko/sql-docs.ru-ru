---
title: ResyncEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2bc43e772ab8f1e330d393461944cb2ecd585149
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711563"
---
# <a name="resyncenum"></a>ResyncEnum
Указывает, перезаписываются ли базовые значения путем вызова [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|По умолчанию. Перезаписывает данные и отложенные обновления будут отменены.|  
|**adResyncUnderlyingValues**|1|Не приводит к перезаписи данных и отложенные обновления не будут отменены.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Resync](../../../ado/reference/ado-api/resync-method.md)
