---
title: XactAttributeEnum | Документы Microsoft
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
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33b3ac42f0e0e175e2dc2571c77f6dbaa962922f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Задает атрибуты транзакции [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|Выполняет сохранение прерываний с помощью вызова [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) для автоматически запускает новую транзакцию. Не все поставщики поддерживают этот режим.|  
|**adXactCommitRetaining**|131072|Выполняет сохранение фиксируется путем вызова [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) автоматический запуск новой транзакции. Не все поставщики поддерживают этот режим.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
