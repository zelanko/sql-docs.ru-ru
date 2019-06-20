---
title: XactAttributeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5bf3c4b8a7cbbee1e384c08746f32d6a7e550ddd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710135"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Указывает атрибуты транзакции [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|Выполняет сохранение прерываний путем вызова [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) автоматически запустить новую транзакцию. Не все поставщики поддерживают такое поведение.|  
|**adXactCommitRetaining**|131072|Выполняет сохранение фиксации путем вызова [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) автоматически запустить новую транзакцию. Не все поставщики поддерживают такое поведение.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
