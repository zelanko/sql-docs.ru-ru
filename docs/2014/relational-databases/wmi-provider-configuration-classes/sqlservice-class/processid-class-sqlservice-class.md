---
title: Класс ProcessId (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2bcc9e31fd70f0201f26751bddbcb3f3f8aeec98
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080926"
---
# <a name="processid-class-sqlservice-class"></a>Класс ProcessId (класс SqlService)
  Возвращает идентификатор системного процесса, уникально определяющий службу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, указывающее идентификатор, уникально определяющий процесс.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
