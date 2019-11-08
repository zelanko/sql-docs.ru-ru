---
title: Метод SetFlag (класс servernetworkprotocolproperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetFlag Method (ServerNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetFlag method
ms.assetid: 95288931-8eb1-4477-ad80-619cf7073e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b341456d2135206083e632b6bbf6dd97f12ca50
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658975"
---
# <a name="setflag-method-servernetworkprotocolproperty-class"></a>Метод SetFlag (класс ServerNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Устанавливает флаг указанного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetFlag(BoolValue)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ServerNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) , который представляет атрибут сетевого протокола для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*булвалуе*|Логическое значение, указывающее новое состояние флага.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
