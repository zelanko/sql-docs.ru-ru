---
title: "Элемент Issue (программа ssbdiagnose) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: efd14c796a0769ebc44d00c2e6e0278bf2d3f3a4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

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
|**Родительский элемент**|[Элемент DiagnosticInformation &#40; ssbdiagnose &#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Дочерние элементы**|None|  
  
## <a name="example"></a>Пример  
 Следующий элемент сообщает об ошибке с номером 1102 для базы данных, в которой отсутствует главный ключ. Ошибка была обнаружена во время анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>См. также:  
 [Программа ssbdiagnose &#40; Компонент Service Broker &#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
