---
title: Метод SetDisable (класс ServerNetworkProtocol) | Документы Microsoft
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
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 486157219bfea29653ff3ba1af0a8c69287ef27c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110111"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a>Метод SetDisable (класс ServerNetworkProtocol)
  Отключает сетевой протокол сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Servernetworkprotocol [класс ServerNetworkProtocol]-class.md), представляющий сетевой протокол, используемый экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  