---
description: Метод ChangePassword (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 94ddd75bddf8845012fe0845826eea264718cc91
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771173"
---
# <a name="changepassword-method-adox"></a>Метод ChangePassword (ADOX)
Изменяет пароль для учетной записи [пользователя](./user-object-adox.md) .  
  
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
  
## <a name="applies-to"></a>Применение  
 [Объект User (ADOX)](./user-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)](./groups-and-users-append-changepassword-methods-example-vb.md)