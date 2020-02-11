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
ms.openlocfilehash: de8baf504a76407037322fd6b799f6d63584eae7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967035"
---
# <a name="changepassword-method-adox"></a>Метод ChangePassword (ADOX)
Изменяет пароль для учетной записи [пользователя](../../../ado/reference/adox-api/user-object-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Параметры  
 *OldPassword*  
 **Строковое** значение, указывающее существующий пароль пользователя. Если у пользователя в данный момент нет пароля, используйте пустую строку ("") для *OldPassword*.  
  
 *NewPassword*  
 **Строковое** значение, указывающее новый пароль.  
  
## <a name="remarks"></a>Remarks  
 По соображениям безопасности старый пароль должен быть указан в дополнение к новому паролю.  
  
 Если поставщик не поддерживает администрирование свойств доверенного лица, возникнет ошибка.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
