---
title: ConnectOptionEnum | Документы Microsoft
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
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 352317f63627038d8b415dce5095aa1570a7f7f8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Указывает ли [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта должны возвращать после установки подключения (синхронно) или перед (асинхронно).  
  
|Константа|Значение|Описание|  
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
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
