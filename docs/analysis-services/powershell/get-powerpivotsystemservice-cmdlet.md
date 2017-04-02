---
title: "Командлет &#171;Get-PowerPivotSystemService&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Командлет &#171;Get-PowerPivotSystemService&#187;
  Возвращает глобальные свойства объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## Синтаксис  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Командлет Get-PowerPivotSystemService возвращает глобальные свойства объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Может быть только один родительский объект на ферму, однако каждая ферма может иметь несколько экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], работающих на разных серверах приложений в ферме. Родительский объект отображает параметры на уровне фермы, которые не зависят от экземпляра. Если ферма включает несколько экземпляров [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, разделенный запятыми список экземпляров покажет, сколько экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] есть в ферме.  
  
## Параметры  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Указывает возвращаемый родительский объект. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
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
C:\PS>Get-PowerPivotSystemService  
```  
  
 В этом примере возвращаются глобальные свойства родительского объекта, при этом отображаются свойства, которые являются общими для всех экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  
  
  