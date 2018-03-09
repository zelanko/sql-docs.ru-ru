---
title: "Open-метод (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c23630224808a70c20583759b6d62c8475ede66a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
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
  
## <a name="remarks"></a>Remarks  
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
