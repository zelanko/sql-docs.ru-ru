---
title: Метод (многомерные Объекты ADO) Open | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 091073431b3ff349b8ae107fcb6a37bfab94e46e
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602784"
---
# <a name="open-method-ado-md"></a>Метод Open (многомерные объекты ADO)
Извлекает результаты многомерного запроса и возвращает результаты, чтобы [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный параметр. Объект **Variant** , имеющего значение допустимого многомерного запроса, например запрос многомерных выражений (MDX). *Источника* аргумент соответствует [источника](../../../ado/reference/ado-md-api/source-property-ado-md.md) свойство. Дополнительные сведения о многомерных Выражениях см. в разделе [OLE DB для оперативной аналитической обработки (OLAP)](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) документации в компонентах Microsoft Data Access SDK.  
  
 *ActiveConnection*  
 Необязательный параметр. Объект **Variant** , результатом которого является строка, указав допустимый ADO [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, имя переменной или определение для подключения. *ActiveConnection* аргумент указывает соединение, в котором следует открыть [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта. Если передать определение подключения для этого аргумента, ADO открывает новое подключение, используя указанные параметры. *ActiveConnection* аргумент соответствует [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) свойство.  
  
## <a name="remarks"></a>Примечания  
 **Откройте** метод выдает ошибку, если ни один из его параметров указан, и его соответствующее значение свойства не задано до попытки открыть **Cellset**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта Cellset (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Свойство ActiveConnection (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close-метод (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство Source (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
