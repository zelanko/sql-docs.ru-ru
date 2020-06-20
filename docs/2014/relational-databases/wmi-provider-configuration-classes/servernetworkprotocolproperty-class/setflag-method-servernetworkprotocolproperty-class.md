---
title: Метод SetFlag (класс класс servernetworkprotocolproperty) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 95288931-8eb1-4477-ad80-619cf7073e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bca152482145b06aaa4aa89fd035812279bff4fa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056799"
---
# <a name="setflag-method-servernetworkprotocolproperty-class"></a>Метод SetFlag (класс ServerNetworkProtocolProperty)
  Устанавливает флаг указанного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetFlag(  
BoolValue  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класс servernetworkprotocolproperty Class] класс servernetworkprotocolproperty-class.md), представляющий атрибут сетевого протокола в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*булвалуе*|Логическое значение, указывающее новое состояние флага.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
