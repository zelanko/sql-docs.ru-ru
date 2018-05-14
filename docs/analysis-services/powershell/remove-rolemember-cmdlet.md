---
title: Командлет remove-RoleMember | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eec431908e2159f7021613c086f1278cb2954b43
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="remove-rolemember-cmdlet"></a>Командлет Remove-RoleMember
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Удаляет член из указанной роли в базе данных служб Analysis Services.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="syntax"></a>Синтаксис  
 `Remove-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Remove-RoleMember [-DatabaseRole] <Microsoft.AnalysisServices.Role> [-MemberName] <System.String>  [<CommonParameters>]`  
  
## <a name="description"></a>Описание  
 Командлет Remove-RoleMember удаляет существующий член из роли в базе данных служб Analysis Services.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-membername-string"></a>-MemberName \<строка >  
 Указывает пользователя или группу Windows, которые удаляются из роли.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-database-string"></a>-Базы данных \<строка >  
 Указывает базу данных, к которой относится роль.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-rolename-string"></a>-RoleName \<строка >  
 Указывает роль, из которой удаляются члены.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|2|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-databaserole-string"></a>-DatabaseRole \<строка >  
 Указывает объект Microsoft.AnalysisServices.Role, из которого будет удален член. Используйте этот параметр, как альтернативу параметрам –Database и –RoleName при необходимости указания роли базы данных через конвейер.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true (ByPropertyName)|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Нет.  
  
## <a name="example-1"></a>Пример 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Эта команда удаляет учетную запись пользователя домена Windows из роли Reader в базе данных AdventureWorks, которая выполняется на локальном экземпляре по умолчанию.  
  
## <a name="example-2"></a>Пример 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 Строка 1 добавляет все роли базы данных из базы данных AWTEST в конвейер. Строка 2, в которой вы набираете $roles, отображает массив ролей. Строка 3 удаляет пользователя Windows «adventure-works\bobh» из первой из ролей в массиве.  
  
## <a name="example-3"></a>Пример 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Remove-rolemember –membername “adventure-works\bobh”  
```  
  
 Эта команда удаляет учетную запись пользователя домена Windows из первой роли в массиве, который создан посредством перечисления дочерних элементов папки Roles в контексте конкретной базы данных (AWTEST).  
  

  
  
