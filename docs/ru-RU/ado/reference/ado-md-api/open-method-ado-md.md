---
title: Open-метод (ADO MD) | Документы Microsoft
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
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38876d744f67ef4c218bb56fd4fa585d9dd8ade3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="open-method-ado-md"></a>Метод Open (ADO MD)
Извлекает результаты многомерного запроса и возвращает результаты в [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **Variant** , результат вычисления которого допустимым многомерного запроса, например запрос многомерных выражений (MDX). *Источника* аргумент соответствует [источника](../../../ado/reference/ado-md-api/source-property-ado-md.md) свойство. Дополнительные сведения о многомерных Выражениях см. в разделе [OLE DB для оперативной аналитической обработки (OLAP)](http://msdn.microsoft.com/en-us/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) документации в компоненты пакете Microsoft Data Access SDK.  
  
 *ActiveConnection*  
 Необязательно. Объект **Variant** , результатом которого является строка, указывающая либо допустимым ADO [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта имени переменной или определения для подключения. *ActiveConnection* аргумент указывает соединение, в котором необходимо открыть [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта. Если передать определение подключения для этого аргумента ADO открывает новое соединение, используя указанные параметры. *ActiveConnection* аргумент соответствует [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) свойство.  
  
## <a name="remarks"></a>Замечания  
 **Откройте** метод создает ошибку, если любой из своих параметров указан, и его соответствующее значение свойства не было задано до попытки открыть **ячеек**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Свойство ActiveConnection (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close-метод (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство Source (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
