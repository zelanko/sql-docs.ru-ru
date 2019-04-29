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
manager: craigg
ms.openlocfilehash: 96268fac4b81230fcb63db6b48ef4ef794abb9c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184142"
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
