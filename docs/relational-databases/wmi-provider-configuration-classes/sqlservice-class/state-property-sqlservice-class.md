---
description: Свойство State (класс SqlService)
title: Свойство State (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a6613da3ef7bcb0405bfa7c89551a08ad5994d0e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537644"
---
# <a name="state-property-sqlservice-class"></a>Свойство State (класс SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает или задает текущее состояние службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее состояние службы.  
  
 Может иметь одно из следующих значений.  
  
 1  
 Остановлена. служба остановлена.  
  
 2  
 Ожидание запуска. Служба ожидает запуска.  
  
 3  
 Ожидание остановки. Служба ожидает остановки.  
  
 4  
 Выполняется. Служба запущена.  
  
 5  
 Ожидание продолжения. Служба ожидает продолжения.  
  
 6  
 Ожидание приостановки. Служба ожидает приостановки.  
  
 7  
 приостановлено Служба приостановлена.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
