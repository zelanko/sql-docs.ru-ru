---
title: ObjectStateEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 41b72647af357bc73eb3e9a2f8c3063f2275f6a6
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707187"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Указывает, является ли объект открытым или закрытым, подключение к источнику данных, выполнение команды или при получении данных.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|Указывает, что данный объект закрыт.|  
|**adStateOpen**|1|Указывает, что объект является открытым.|  
|**adStateConnecting**|2|Указывает, что объект подключается.|  
|**adStateExecuting**|4|Указывает, что объект выполняет команду.|  
|**adStateFetching**|8|Указывает, что извлекаются строки объекта.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[Свойство State (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
