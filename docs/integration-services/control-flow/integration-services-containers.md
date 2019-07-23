---
title: Контейнеры служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS containers
- containers [Integration Services]
- containers [Integration Services], about containers
- control flow [Integration Services], containers
- SQL Server Integration Services containers
ms.assetid: 1b725922-ec59-4a47-9d55-e079463058f3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 13695f6226331455754839a5e26198ae49d186c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67929862"
---
# <a name="integration-services-containers"></a>Контейнеры служб Integration Services

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Контейнеры в службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] представляют собой объекты, содержащие структуру пакетов и службы для задач. Они поддерживают повторение потоков управления в пакетах, а также группируют задачи и контейнеры в единые рабочие объекты. Кроме задач контейнеры могут включать другие контейнеры.  
  
 Пакеты используют контейнеры для следующих целей.  
  
-   Повторение задач для каждого элемента коллекции: файлов, папок, схем или управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO). Например, пакет может выполнять инструкции Transact-SQL, размещенные в нескольких файлах.  
  
-   Повторение задач до тех пор, пока значение определенного выражения не будет равно **false**. Например, пакет может посылать разные сообщения по электронной почте семь раз, один раз в каждый день недели.  
  
-   Группирование задач и контейнеров, успешное или аварийное выполнение которых учитывается как для единого объекта. Например, пакет может группировать задачи, удаляющие и добавляющие строки в таблице базы данных, а затем фиксировать их или же производить откат всех задач в случае сбоя одной из них.  
  
## <a name="container-types"></a>Типы контейнеров  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] поддерживают четыре типа контейнеров для построения пакетов. В следующей таблице перечислены типы контейнеров.  
  
|Контейнер|Описание|  
|---------------|-----------------|  
|[Контейнер «цикл по каждому элементу»](../../integration-services/control-flow/foreach-loop-container.md)|Повторяет запуск потока управления для каждого элемента, используя перечислитель.|  
|[Контейнер «цикл по элементам»](../../integration-services/control-flow/for-loop-container.md)|Повторяет запуск потока управления с проверкой условия.|  
|[Контейнер последовательности](../../integration-services/control-flow/sequence-container.md)|Группирует задачи и контейнеры в потоки управления, являющиеся частью потока управления пакета.|  
|[Контейнер «Сервер задач»](../../integration-services/control-flow/task-host-container.md)|Обеспечивает поддержку служб для отдельной задачи.|  
  
 Пакеты и обработчики событий также являются типами контейнеров. Дополнительные сведения см. в разделах [Пакеты служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-packages.md) and [Обработчики событий в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-event-handlers.md).  
  
### <a name="summary-of-container-properties"></a>Сводка свойств контейнера  
 Все типы контейнеров имеют набор общих свойств. При создании пакетов с помощью графических средств, предоставляемых службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , в окне «Свойства» перечисляются следующие свойства контейнеров «цикл по каждому элементу», «цикл по элементам» и контейнеров последовательности. Настройка свойств контейнера сервера задач является частью настройки задачи, которую инкапсулирует сервер задач. При настройке задачи настраиваются и свойства сервера задачи.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|**DelayValidation**|Логическое значение, указывающее, откладывается ли проверка контейнера до времени выполнения. Значение этого свойства по умолчанию — **False**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>.|  
|**Описание**|Описание контейнера. Свойство содержит строку, но может быть пустым.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>.|  
|**Отключить**|Логическое значение, указывающее, запущен ли контейнер. Значение этого свойства по умолчанию — **False**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>.|  
|**DisableEventHandlers**|Логическое значение, указывающее, связаны ли обработчики событий с запуском контейнера. Значение этого свойства по умолчанию — **False**.|  
|**FailPackageOnFailure**|Логическое значение, указывающее, завершается ли работа пакета с ошибкой в случае ошибки в контейнере. Значение этого свойства по умолчанию — **False**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>.|  
|**FailParentOnFailure**|Логическое значение, указывающее, завершается ли работа родительского контейнера с ошибкой в случае ошибки в контейнере. Значение этого свойства по умолчанию — **False**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>.|  
|**ForcedExecutionValue**|Если свойство **ForceExecutionValue** равно **True**, объект содержит необязательное значение выполнения для контейнера. Значение этого свойства по умолчанию равно **0**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>.|  
|**ForcedExecutionValueType**|Тип данных **ForcedExecutionValue**. Значение по умолчанию этого свойства равно **Int32**.|  
|**ForceExecutionResult**|Значение, определяющее вынужденный результат запуска пакета или контейнера. Допустимые значения: **None**, **Success**, **Failure**и **Completion**. Значение этого свойства по умолчанию — **None**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>.|  
|**ForceExecutionValue**|Логическое значение, указывающее, должно ли необязательное значение выполнения для контейнера содержать конкретное значение. Это свойство имеет значение по умолчанию **False**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>.|  
|**Идентификатор**|Идентификатор GUID контейнера, назначаемый ему при создании пакета. Это свойство доступно только для чтения.<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.|  
|**IsolationLevel**|Уровень изоляции транзакции контейнера. Допустимые значения — **Unspecified**, **Chaos**, **ReadUncommitted**, **ReadCommitted**, **RepeatableRead**, **Serializable**и **Snapshot**. Значение по умолчанию этого свойства равно **Serializable**. Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.|  
|**LocaleID**|Локаль Microsoft Win32. Значение этого свойства по умолчанию равно локали операционной системы на локальном компьютере.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>.|  
|**LoggingMode**|Значение, определяющее для контейнера режим записи в журнал. Допустимые значения — **Disabled**, **Enabled**и **UseParentSetting**. Значение по умолчанию этого свойства равно **UseParentSetting**. Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.|  
|**MaximumErrorCount**|Максимальное число ошибок, после достижения которого выполнение контейнера прекращается. Значение этого свойства по умолчанию равно **1**.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>.|  
|**Название**|Имя контейнера.<br /><br /> Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>.|  
|**TransactionOption**|Участие контейнера в транзакции. Допустимые значения — **NotSupported**, **Supported**, **Required**. Значение по умолчанию этого свойства равно **Supported**. Дополнительные сведения см. в статье <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.|  
  
 Чтобы узнать о всех свойствах, доступных для контейнеров «цикл по каждому элементу», «цикл по элементам», контейнеров последовательности и сервера задач при настройке свойств программно, см. следующие разделы по API-интерфейсу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] :  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.Sequence  
  
-   T:Microsoft.SqlServer.Dts.Runtime.TaskHost  
  
## <a name="objects-that-extend-container-functionality"></a>Объекты, расширяющие функциональные возможности контейнеров  
 Контейнеры включают в себя потоки управления, которые состоят из исполняемых объектов и ограничений очередностью, а также могут использовать обработчики событий и переменные. Контейнер сервера задач является исключением из правила: так как он инкапсулирует единственную задачу, не используется никаких элементов управления очередностью.  
  
### <a name="executables"></a>Исполняемые объекты  
 Исполняемыми объектами называются задачи уровня контейнера, а также любые контейнеры внутри контейнера. Исполняемый объект может быть одной из задач или одним из контейнеров, изначально включенных в службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , либо пользовательской задачей. Дополнительные сведения см. в статье [Integration Services Tasks](../../integration-services/control-flow/integration-services-tasks.md).  
  
### <a name="precedence-constraints"></a>Управление очередностью  
 Элементы управления очередностью связывают контейнеры и задачи из одного родительского контейнера в упорядоченный поток управления. Дополнительные сведения см. в статье [Precedence Constraints](../../integration-services/control-flow/precedence-constraints.md).  
  
### <a name="event-handlers"></a>Обработчики событий  
 Обработчики события на уровне контейнера реагируют на события, инициируемые контейнером или объектами, содержащимися в нем. Дополнительные сведения см. в разделе [Обработчики событий в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-event-handlers.md).  
  
### <a name="variables"></a>Переменные  
 Переменные, используемые в контейнерах, включают системные переменные уровня контейнера, предоставляемые службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], а также пользовательские переменные, используемые контейнером. Дополнительные сведения см. в разделе [Переменные служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md).  
  
## <a name="break-points"></a>Точки останова  
 Если задается точка останова в контейнере и условием останова является **Приостановить выполнение при получении контейнером события OnVariableValueChanged**, определите переменную в области контейнера.  
  
## <a name="see-also"></a>См. также:  
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  
