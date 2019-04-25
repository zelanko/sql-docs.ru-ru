---
title: Метод SetCurrentCertificate (класс ServerSettings) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetCurrentCertificate Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: f9c6e172-11be-42de-b19b-a5b3436e84da
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6d3cb9ed5696351f1c2c66a035c920940615ecfe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62515790"
---
# <a name="setcurrentcertificate-method-serversettings-class"></a>Метод SetCurrentCertificate (класс ServerSettings)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Задает текущий сертификат безопасности.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [ServerSettings](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) , представляющий настройки сервера на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*SHA*|Строковое значение, указывающее текущий сертификат безопасности.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
