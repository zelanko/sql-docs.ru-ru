---
title: "Элемент DiagnosticInformation (программа ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "формат выходного XML-файла [ssbdiagnose], элемент diagnosticinformation"
  - "diagnosticinformation, элемент"
  - "ssbdiagnose"
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Элемент DiagnosticInformation (программа ssbdiagnose)
  В элементе **DiagnosticInformation** содержатся все элементы, сообщающие о диагностических данных, обнаруженных программой. **DiagnosticInformation** — корневой элемент выходного XML-файла программы **ssbdiagnostic** .  
  
## Синтаксис  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## Атрибуты элемента  
  
|Attribute|Описание|  
|---------------|-----------------|  
|**None**|Недоступно|  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Один раз на выходной XML-файла программы **ssbdiagnose** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|Нет.|  
|**Дочерние элементы**|[Элемент Banner (программа ssbdiagnose)](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)<br /><br /> [Элемент Issue (программа ssbdiagnose)](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)|  
  
## Замечания  
 Дополнительные сведения о пространствах имен XML см. в статье [Пространства имен в XML-документе](http://go.microsoft.com/fwlink/?LinkId=7341) в библиотеке [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN.  
  
## См. также:  
 [Служебная программа ssbdiagnose (компонент Service Broker)](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  