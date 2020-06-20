---
title: Метод SetValue (класс класс clientsettingsgeneralflag) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: e53d7c31c702531e58f4f950e2053989d1f9de05
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067897"
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
|*Значение*|Логическое значение, указывающее состояние флага.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
