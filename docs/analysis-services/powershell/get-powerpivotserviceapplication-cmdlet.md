---
title: "Командлет &#171;Get-PowerPivotServiceApplication&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Командлет &#171;Get-PowerPivotServiceApplication&#187;
  Возвращает одно или несколько приложений службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## Синтаксис  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Командлет Get-PowerPivotServiceApplication возвращает приложение службы, указанное параметром Identity. Если параметр не указан, командлет возвращает все приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Каждое приложение идентифицируется отображаемым именем, типом и идентификатором GUID. Для просмотра дополнительных свойств приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] добавьте в командлет параметр format-list.  
  
## Параметры  
  
### -Identity \<SPGeminiServiceApplicationPipeBind>  
 Указывает возвращаемое приложение службы. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### \<Общие параметры>  
 Этот командлет поддерживает общие параметры: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer и OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
## Пример 1  
  
```  
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 В этом примере возвращается одно или несколько приложений службы в ферме.  
  
## Пример 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 Этот пример возвращает все свойства приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## Пример 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 В этом примере возвращается одно приложение службы, при этом отображается его имя, тип и идентификатор GUID. Если отображаемое имя слишком длинное, оно будет усечено. Для просмотра полного имени воспользуйтесь параметром format-list.  
  
  