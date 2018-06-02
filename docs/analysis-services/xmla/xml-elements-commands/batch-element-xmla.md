---
title: Пакетное элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4644b8775212eae0cb6d912df9bc415c5fc96ec7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573946"
---
# <a name="batch-element-xmla"></a>Элемент Batch (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Выполняет один или несколько XML для аналитики (XMLA) команды как пакетная операция последовательно или параллельно на экземпляре служб Analysis Services.  
  
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
  
|attribute|Описание|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Необязательный атрибут **Boolean** ) Показывает, будут ли обработаны все объекты, которые нуждаются в повторной обработке.<br /><br /> Если задано значение true, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр обрабатывает все объекты, которые требуют была вызвана обработкой объекта, включенного в **пакета** команды.<br /><br /> Если значение **false**, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр обрабатывает только те объекты, включенные в **пакета** команды.|  
|Transaction|(Необязательный атрибут **Boolean** ) Показывает, будут ли команды, включенные в команду **Batch** , обрабатываться в одной транзакции или они будут обрабатываться как индивидуальные транзакции.<br /><br /> Если установлено значение true, то все команды, которые были включены в команду **Batch** , считаются одной транзакцией. Если любая из команд завершается неуспешно, то происходит откат команд, выполненных до появления ошибки, а выполнение команды **Batch** останавливается без выполнения дальнейших команд.<br /><br /> Если установлено значение **false**, то команда **Batch** пытается выполнить каждую команду; результаты каждой успешно выполненной команды фиксируются.|  
  
## <a name="remarks"></a>Примечания  
  
> [!WARNING]  
>  Команда, выполнение или инструкция в настоящее время не поддерживается в пакетной операции.  
  
 Дополнительные сведения о выполнении пакетных операций в XML для Аналитики см. в разделе [выполнение пакетных операций &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
