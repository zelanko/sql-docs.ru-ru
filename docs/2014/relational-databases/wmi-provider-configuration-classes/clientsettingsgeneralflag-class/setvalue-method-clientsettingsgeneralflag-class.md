---
title: Метод SetValue (класс ClientSettingsGeneralFlag) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 708d87e93556e05cde2f122ecf07c7982f1b4360
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080934"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a>Метод SetValue (класс ClientSettingsGeneralFlag)
  Задает все значения упоминаемого флага.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ClientSettingsGeneralFlag](clientsettingsgeneralflag-class.md) , представляющий универсальный флаг для параметров сервера.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*Value*|Логическое значение, указывающее состояние флага.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
