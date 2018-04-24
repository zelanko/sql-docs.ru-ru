---
title: Метод ChangePassword (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d88391c197a7d7fe0b112efa069d4f00c4f074bc
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
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
  
 *newPassword*  
 Объект **строка** значение, указывающее новый пароль.  
  
## <a name="remarks"></a>Замечания  
 По соображениям безопасности помимо новый пароль необходимо указать старый пароль.  
  
 Если поставщик не поддерживает администрирование свойств доверенное лицо, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
