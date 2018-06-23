---
title: Свойство AcceptStop (класс SqlService) | Документы Microsoft
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
- AcceptStop Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19197db0e6d2679d0ad13bcb43472be4448fccb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102364"
---
# <a name="acceptstop-property-sqlservice-class"></a>Свойство AcceptStop (класс SqlService)
  Возвращает логическое значение, определяющее, можно ли остановить службу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.AcceptStop [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класс SqlService](sqlservice-class.md) объект, представляющий службу  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, определяющее, можно ли остановить службу: `true`, если можно; в противном случае — `false`.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  