---
title: Свойство PropertyValType (класс ServerNetworkProtocolProperty) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4a69cb8f0817c086537381a87b96dfb237b8d59c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62643194"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>Свойство PropertyValType (класс ServerNetworkProtocolProperty)
  Возвращает тип данных значения, хранящегося в указанном свойстве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ServerNetworkProtocolProperty](servernetworkprotocolproperty-class.md) , который представляет атрибут сетевого протокола для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, представляющее тип данных для значения свойства. Возвращает 0 для строкового значения и 1 для числового типа.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
