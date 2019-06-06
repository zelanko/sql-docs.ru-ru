---
title: Метод ChangePassword (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 981f2e5b801cd35b0aedb04e5f1aa11b741e4535
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66708003"
---
# <a name="changepassword-method-adox"></a>Метод ChangePassword (ADOX)
Изменяет пароль для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) учетной записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Параметры  
 *OldPassword*  
 Объект **строка** значение, указывающее существующий пароль пользователя. Если у пользователя нет в настоящее время пароль, использовать пустую строку ("») для *OldPassword*.  
  
 *Задает новый пароль*  
 Объект **строка** значение, указывающее новый пароль.  
  
## <a name="remarks"></a>Примечания  
 По соображениям безопасности необходимо указать старый пароль в дополнение к новый пароль.  
  
 Если поставщик не поддерживает администрирование свойства доверенное лицо, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
