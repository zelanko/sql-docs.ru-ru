---
title: Событие FetchProgress (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9f7b31524a6c54846072fdce8cca76189c7034ad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698083"
---
# <a name="fetchprogress-event-ado"></a>Событие FetchProgress (ADO)
**FetchProgress**событий вызывается периодически во время длительной операции асинхронного сообщить, сколько больше строк в настоящее время были извлечены в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *Ход выполнения*  
 Объект **Long** значение, указывающее количество записей, которые в настоящее время после извлечения пользователем операции выборки.  
  
 *MaxProgress*  
 Объект **Long** должен получить значение, указывающее максимальное количество записей.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 *pRecordset*  
 Объект **записей** объект, являющийся объектом, для которого извлекаются записи.  
  
## <a name="remarks"></a>Примечания  
 При использовании **FetchProgress** с дочерним **набор записей**, имейте в виду, что *ход выполнения* и *MaxProgress* значения параметров являются производными из основного [служба курсора](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) набора строк. Значения, возвращаемые представляют общее число записей в базовом наборе строк, не только количество записей в текущем.  
  
> [!NOTE]
>  Чтобы использовать **FetchProgress** с Microsoft Visual Basic, Visual Basic 6.0 или более поздней версии необходим.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
