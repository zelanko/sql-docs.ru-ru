---
title: "Элемент Issue (программа ssbdiagnose) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 560df4e8124448a3b3672e9603ef9506572c71be
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="issue-element-ssbdiagnose"></a>Элемент Issue (программа ssbdiagnose)
  Сообщает о проблеме, обнаруженной программой **ssbdiagnose** . В выходном XML-файле программы **ssbdiagnose** для каждой из обнаруженных проблем присутствует один элемент Issue.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|Attribute|Описание|  
|---------------|-----------------|  
|**type**|Определяет категорию проблемы, о которой сообщает элемент Issue:<br /><br /> **"Diagnosis"** . Сообщает о проблеме, обнаруженной во время анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **Problem** . Сообщает о проблеме, в результате которой программе **ssbdiagnose** не удалось завершить анализ. Устраните проблему и снова запустите программу **ssbdiagnose**.<br /><br /> **Event** . Сообщает о событии приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , обнаруженном во время выполнения проверки **-RUNTIME** . События включаются в отчет, только если указан параметр **-SHOWEVENTS** .|  
|**код**|Определяет номер ошибки для сообщения.|  
|**сервер**|Определяет экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , в котором обнаружена проблема. Если проблема произошла в экземпляре по умолчанию, то в атрибуте server будет указано только имя компьютера. Если проблема произошла в именованном экземпляре, то атрибут server будет иметь значение в формате «ИмяКомпьютера\ИмяЭкземпляра».|  
|**базой данных**|Определяет имя базы данных, в которой обнаружена проблема.|  
|**объект**|Определяет имя объекта, в котором обнаружена проблема. Если неполадка произошла на уровне экземпляра или базы данных, то в атрибуте object повторяется имя экземпляра или базы данных.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение**|Возвращает текст сообщения об ошибке.|  
|**Применяемость**|Один раз для каждой ошибки.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DiagnosticInformation (программа ssbdiagnose)](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Дочерние элементы**|None|  
  
## <a name="example"></a>Пример  
 Следующий элемент сообщает об ошибке с номером 1102 для базы данных, в которой отсутствует главный ключ. Ошибка была обнаружена во время анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>См. также:  
 [Программа ssbdiagnose (компонент Service Broker)](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
