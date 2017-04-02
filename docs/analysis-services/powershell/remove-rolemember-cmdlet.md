---
title: "Командлет Remove-RoleMember | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e38f56ab-facd-4bef-9502-f52f8486a6a6
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Командлет Remove-RoleMember
  Удаляет член из указанной роли в базе данных служб Analysis Services.  
  
## Синтаксис  
 `Remove-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Remove-RoleMember [-DatabaseRole] <Microsoft.AnalysisServices.Role> [-MemberName] <System.String>  [<CommonParameters>]`  
  
## Description  
 Командлет Remove-RoleMember удаляет существующий член из роли в базе данных служб Analysis Services.  
  
## Параметры  
  
### -MemberName \<строка>  
 Указывает пользователя или группу Windows, которые удаляются из роли.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Database \<строка>  
 Указывает базу данных, к которой относится роль.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -RoleName \<строка>  
 Указывает роль, из которой удаляются члены.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|2|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -DatabaseRole \<строка>  
 Указывает объект Microsoft.AnalysisServices.Role, из которого будет удален член. Используйте этот параметр, как альтернативу параметрам –Database и –RoleName при необходимости указания роли базы данных через конвейер.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true (ByPropertyName)|  
|Принимать символы-шаблоны?|false|  
  
### \<Общие параметры>  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Входы и выходы  
 Нет.  
  
## Пример 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Эта команда удаляет учетную запись пользователя домена Windows из роли Reader в базе данных AdventureWorks, которая выполняется на локальном экземпляре по умолчанию.  
  
## Пример 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 Строка 1 добавляет все роли базы данных из базы данных AWTEST в конвейер. Строка 2, в которой вы набираете $roles, отображает массив ролей. Строка 3 удаляет пользователя Windows «adventure-works\bobh» из первой из ролей в массиве.  
  
## Пример 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Remove-rolemember –membername “adventure-works\bobh”  
```  
  
 Эта команда удаляет учетную запись пользователя домена Windows из первой роли в массиве, который создан посредством перечисления дочерних элементов папки Roles в контексте конкретной базы данных (AWTEST).  
  
## См. также  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Управление табличными моделями с помощью PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  