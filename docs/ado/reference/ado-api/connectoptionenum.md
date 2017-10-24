---
title: "ConnectOptionEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 582f85d3ce45071cd283f05f5d595e10b5d1614c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Указывает ли [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта должны возвращать после установки подключения (синхронно) или перед (асинхронно).  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Открывается соединение асинхронно. [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) событие может использоваться для определения, когда подключение станет доступным.|  
|**adConnectUnspecified**|-1|По умолчанию. Открывает подключение синхронно.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)

