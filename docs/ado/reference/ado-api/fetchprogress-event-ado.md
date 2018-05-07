---
title: Событие FetchProgress (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fea26975fc162f92527f63123eddb95fade8a8e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fetchprogress-event-ado"></a>Событие FetchProgress (ADO)
**FetchProgress**событие вызывается периодически во время продолжительной операции асинхронного сообщить, сколько дополнительные строки в данный момент были получены в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *Ход выполнения*  
 Объект **длинные** значение, указывающее количество записей, которые в настоящее время после извлечения пользователем операции выборки.  
  
 *MaxProgress*  
 Объект **длинные** должно получить значение, указывающее максимальное количество записей.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 *pRecordset*  
 Объект **записей** объект, являющийся объектом, для которого извлекаются записи.  
  
## <a name="remarks"></a>Замечания  
 При использовании **FetchProgress** с дочерним **записей**, имейте в виду, *выполняется* и *MaxProgress* производных значений параметров из основного [службы курсора](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) набора строк. Возвращаемые значения представляют общее количество записей в базовом наборе строк, не только число записей в текущем.  
  
> [!NOTE]
>  Для использования **FetchProgress** с помощью Microsoft Visual Basic, Visual Basic 6.0 или более поздней версии не требуется.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
