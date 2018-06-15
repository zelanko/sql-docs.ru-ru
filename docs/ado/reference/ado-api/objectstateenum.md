---
title: ObjectStateEnum | Документы Microsoft
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
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46030a27b9a2567f023c2c0d7946536703c91195
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279986"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Указывает, является ли объект открытым или закрытым, соединение с источником данных, выполнение команды или при получении данных.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|Указывает, что данный объект закрыт.|  
|**adStateOpen**|1|Указывает, что объект является открытым.|  
|**adStateConnecting**|2|Указывает, что объект подключается.|  
|**adStateExecuting**|4|Указывает, что объект является выполнение команды.|  
|**adStateFetching**|8|Указывает, происходит поиск строки объекта.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
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
