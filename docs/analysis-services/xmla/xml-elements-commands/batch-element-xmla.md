---
title: "Пакетное элемент (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Batch Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords:
- Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 72ba969247e7e6ff86013c1c875f4486884268c5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="batch-element-xmla"></a>Элемент Batch (XML для аналитики)
  Выполняет один или несколько XML для аналитики (XMLA) команды как пакетная операция последовательно или параллельно на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Batch Transaction="Boolean" ProcessAffectedObjects="Boolean">  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <Parallel>...</Parallel>  
      <!-- One or more XMLA commands -->  
   </Batch>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Привязки](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md), [DataSourceView](../../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md), [параллельных](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)<br /><br /> Один или несколько из следующих команд XML для Аналитики: [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [ CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), [создания](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md), [удаление](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [Вставить](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [блокировки](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [Восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [инструкции](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md), [подписаться](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [Синхронизации](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md), [разблокировать](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md), [обновление](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Необязательный атрибут **Boolean** ) Показывает, будут ли обработаны все объекты, которые нуждаются в повторной обработке.<br /><br /> Если задано значение true, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр обрабатывает все объекты, которые требуют была вызвана обработкой объекта, включенного в **пакета** команды.<br /><br /> Если значение **false**, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр обрабатывает только те объекты, включенные в **пакета** команды.|  
|Transaction|(Необязательный атрибут **Boolean** ) Показывает, будут ли команды, включенные в команду **Batch** , обрабатываться в одной транзакции или они будут обрабатываться как индивидуальные транзакции.<br /><br /> Если установлено значение true, то все команды, которые были включены в команду **Batch** , считаются одной транзакцией. Если любая из команд завершается неуспешно, то происходит откат команд, выполненных до появления ошибки, а выполнение команды **Batch** останавливается без выполнения дальнейших команд.<br /><br /> Если установлено значение **false**, то команда **Batch** пытается выполнить каждую команду; результаты каждой успешно выполненной команды фиксируются.|  
  
## <a name="remarks"></a>Замечания  
  
> [!WARNING]  
>  Команда, выполнение или инструкция в настоящее время не поддерживается в пакетной операции.  
  
 Дополнительные сведения о выполнении пакетных операций в XML для Аналитики см. в разделе [выполнение пакетных операций &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

