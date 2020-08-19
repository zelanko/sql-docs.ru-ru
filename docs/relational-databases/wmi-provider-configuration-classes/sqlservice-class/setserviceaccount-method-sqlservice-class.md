---
description: Метод SetServiceAccount (класс SqlService)
title: Метод SetServiceAccount (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 898d6a1eae5cf82915bc4647690b3ce991aa3352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460051"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Метод SetServiceAccount (класс SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Пытается изменить имя пользователя и пароль, с которыми выполняется экземпляр службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
#### <a name="parameters"></a>Параметры  
 *сервицестартнаме*  
 Строковое значение, указывающее имя учетной записи, под которым выполняется служба. В зависимости от типа службы имя учетной записи может иметь формат ИмяДомена\ИмяПользователя. При запуске процесс службы входит в систему, используя один из следующих двух форматов:  
  
-   если учетная запись принадлежит встроенному домену, можно указать \ИмяПользователя;  
  
-   Если указано значение NULL, служба будет входить в систему как учетная запись **LocalSystem** .  
  
 Для драйверов ядра или системного уровня значение *StartName* содержит имя объекта Driver, \Филесистем\рдр или \дривер\кснс, которое используется системой ввода-вывода для загрузки драйвера устройства. Если задано значение NULL, драйвер выполняется с именем объекта «значение по умолчанию», созданным системой ввода-вывода на основе имени службы, например DWDOM\Admin.  
  
 *сервицестартпассворд*  
 Строковое значение, указывающее пароль для имени учетной записи в параметре *StartName* . Если пароль не меняется, указывается значение NULL. Если служба не имеет пароля, указывается пустая строка.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
