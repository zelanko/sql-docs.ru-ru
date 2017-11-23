---
title: "Метод ChangePassword (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords: ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33f2bfdc111277ef035aa8e3cde36f019a97f5b4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="changepassword-method-adox"></a>Метод ChangePassword (ADOX)
Изменяет пароль для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) учетной записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Параметры  
 *Старый_пароль*  
 Объект **строка** значение, указывающее существующий пароль пользователя. Если у пользователя нет в настоящее время пароль, следует использовать пустую строку ("») для *Старый_пароль*.  
  
 *NewPassword*  
 Объект **строка** значение, указывающее новый пароль.  
  
## <a name="remarks"></a>Замечания  
 По соображениям безопасности помимо новый пароль необходимо указать старый пароль.  
  
 Если поставщик не поддерживает администрирование свойств доверенное лицо, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
