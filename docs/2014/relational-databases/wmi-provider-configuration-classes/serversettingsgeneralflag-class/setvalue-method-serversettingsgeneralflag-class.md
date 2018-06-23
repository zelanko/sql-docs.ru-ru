---
title: Метод SetValue (класс Serversettingsgeneralflag) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SetValue Method (ServerSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dc8bec3f0060e7c69ec5d0d15ed4a6f5aecd1a8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191943"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a>Метод SetValue (класс ServerSettingsGeneralFlag)
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
 Объект [класса ServerSettingsGeneralFlag](serversettingsgeneralflag-class.md) , представляющий универсальный флаг для параметров сервера.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*Value*|Логическое значение, указывающее состояние флага.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  