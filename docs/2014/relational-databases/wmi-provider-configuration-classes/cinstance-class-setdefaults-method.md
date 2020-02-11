---
title: Метод SetDefaults (класс CInstance) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2a105fd636c454ab236764611f1e57729ccad6ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63192441"
---
# <a name="setdefaults-method-cinstance-class"></a>Метод SetDefaults (класс CInstance)
  Задает все значения по умолчанию для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента с возможностью перезаписи существующих данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 Объект [класса CInstance](cinstance-class.md) , представляющий экземпляр клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Description|  
|---------------|-----------------|  
|*овервритеалл*|Логическое значение, указывающее, следует ли перезаписывать существующие значения в экземпляре клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. `true`, если следует; в противном случае — `false`.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
