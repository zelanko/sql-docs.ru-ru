---
title: Метод RemoveCertificate (класс SInstance) | Документы Microsoft
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
- RemoveCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 7e5dbafa-a634-4617-9622-510514fce0ce
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2a2854c7ecf62565a8cb9099382a72f9ab00bde8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192410"
---
# <a name="removecertificate-method-sinstance-class"></a>Метод RemoveCertificate (класс SInstance)
  Удаляет текущий сертификат безопасности из экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SInstance](sinstance-class.md) , представляющий параметры сервера в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  