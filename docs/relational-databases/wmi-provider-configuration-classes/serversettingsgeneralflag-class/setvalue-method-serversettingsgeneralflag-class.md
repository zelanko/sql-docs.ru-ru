---
title: Метод SetValue (класс ServerSettingsGeneralFlag) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- SetValue Method (ServerSettingsGeneralFlag Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 84a7a3ff97f4d5931c4781b4a6c780f0189992cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779712"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a>Метод SetValue (класс ServerSettingsGeneralFlag)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Задает все значения упоминаемого флага.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetValue(Value)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ServerSettingsGeneralFlag](../../../relational-databases/wmi-provider-configuration-classes/serversettingsgeneralflag-class/serversettingsgeneralflag-class.md) , представляющий универсальный флаг для параметров сервера.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*Value*|Логическое значение, указывающее состояние флага.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
