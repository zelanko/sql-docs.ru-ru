---
title: Элемент Issue
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 3a91cf0575cb84a744925b7b60be0146a4d9ec5f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254193"
---
# <a name="issue-element-ssbdiagnose"></a>Элемент Issue (программа ssbdiagnose)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
  
|attribute|Description|  
|---------------|-----------------|  
|**type**|Определяет категорию проблемы, о которой сообщает элемент Issue:<br /><br /> **"Diagnosis"** . Сообщает о проблеме, обнаруженной во время анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **Problem** . Сообщает о проблеме, в результате которой программе **ssbdiagnose** не удалось завершить анализ. Устраните проблему и снова запустите программу **ssbdiagnose**.<br /><br /> **Event** . Сообщает о событии приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , обнаруженном во время выполнения проверки **-RUNTIME** . События включаются в отчет, только если указан параметр **-SHOWEVENTS** .|  
|**code**|Определяет номер ошибки для сообщения.|  
|**server**|Определяет экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , в котором обнаружена проблема. Если проблема произошла в экземпляре по умолчанию, то в атрибуте server будет указано только имя компьютера. Если проблема произошла в именованном экземпляре, то атрибут server будет иметь значение в формате «ИмяКомпьютера\ИмяЭкземпляра».|  
|**database**|Определяет имя базы данных, в которой обнаружена проблема.|  
|**object**|Определяет имя объекта, в котором обнаружена проблема. Если неполадка произошла на уровне экземпляра или базы данных, то в атрибуте object повторяется имя экземпляра или базы данных.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Value**|Возвращает текст сообщения об ошибке.|  
|**Наличие**|Один раз для каждой ошибки.|  
  
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
  
  
