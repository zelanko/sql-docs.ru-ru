---
title: Метод SetEnable (класс класс clientnetworkprotocol) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: a66c756a-1311-4f4a-8088-818f8ed90056
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dfba695506dd04ded82083b85bfbb751913fbcbb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061437"
---
# <a name="setenable-method-clientnetworkprotocol-class"></a>Метод SetEnable (класс ClientNetworkProtocol)
  Включает сетевой протокол клиента, указанный в параметре [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetEnableMethod()  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Настройка сетевых протоколов клиента и сетевых библиотек](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
