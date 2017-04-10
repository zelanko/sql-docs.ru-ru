---
title: "Командлет &#171;Get-PowerPivotSystemServiceInstance&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56027a8e-1949-4349-b616-68c8b1d2963c
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Командлет &#171;Get-PowerPivotSystemServiceInstance&#187;
  Возвращает один или несколько экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , работающих на серверах приложений в ферме.  
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## Синтаксис  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Командлет Get-PowerPivotSystemServiceInstance возвращает свойства одного или нескольких экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], работающих в ферме. Командлет сообщает тип приложения, состояние (в сети или вне сети) и удостоверение. Для просмотра дополнительных свойств определенного экземпляра добавьте в командлет параметры Identity и format-list.  
  
## Параметры  
  
### -Identity \<PowerPivotMidTierServiceInstancePipeBind>  
 Указывает возвращаемый экземпляр служб. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### \<Общие параметры>  
 Этот командлет поддерживает общие параметры: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer и OutVariable. Дополнительные сведения см. в разделе [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
## Пример 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 В этом примере возвращаются дополнительные свойства указанного экземпляра, включая имя сервера, версию и состояние обновления.  
  
  