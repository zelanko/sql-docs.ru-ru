---
title: Свойство dependencies (класс SqlService) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ef112eb58b15632dea35d709f146ffab6905cae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188179"
---
# <a name="dependencies-property-sqlservice-class"></a>Свойство Dependencies (класс SqlService)
  Возвращает список служб, зависимых от указанной службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив значений string[], содержащий список служб, зависимых от указанной службы.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  