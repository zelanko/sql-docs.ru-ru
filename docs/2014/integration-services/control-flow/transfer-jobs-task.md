---
title: Задача "Передача заданий" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.f1
helpviewer_keywords:
- Transfer Jobs task [Integration Services]
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ef0ed6a2af2d48010550997d7ba216a91f2728f5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296994"
---
# <a name="transfer-jobs-task"></a>Задача «Передача заданий»
  Задача «Передача заданий» служит для передачи одного или нескольких заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Задачу «Передача заданий» можно настроить на передачу всех или только определенных заданий. Можно также указать, будут ли переданные задания доступны в месте назначения.  
  
 Задания, подлежащие передаче, могут уже существовать в месте назначения. Задачу «Передача заданий» можно настроить на обработку существующих задач одним из следующих способов:  
  
-   Перезаписать существующие задания.  
  
-   Аварийно завершить задачу при наличии дубликатов заданий.  
  
-   Пропустить дубликаты заданий.  
  
 Во время выполнения задача «Передача заданий» подключается к исходному и целевому серверу, используя один или два диспетчера соединений SMO. Диспетчер соединений SMO настраивается независимо от задачи «Передача заданий», но задача будет на него ссылаться. Диспетчер соединений SMO определяет сервер и режим проверки подлинности, используемый для доступа к серверу. Дополнительные сведения см. в статье [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
## <a name="transferring-jobs-between-instances-of-sql-server"></a>Передача заданий между экземплярами SQL Server  
 Задача «Передача заданий» поддерживает исходные серверы и серверы назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ограничений в отношении использования определенных версий источника или целевого объекта не существует.  
  
## <a name="events"></a>События  
 Задача «Передача заданий» инициирует уведомляющее событие, сообщающее число переданных заданий, а также событие-предупреждение в случае, когда задание перезаписывается. Задача не сообщает о ходе передачи задания; она сообщает лишь о выполнении 0% и 100%.  
  
## <a name="execution-value"></a>Значение выполнения  
 Значение выполнения, определяемое свойством `ExecutionValue` задачи, возвращает число переданных заданий. Назначив пользовательскую переменную, чтобы `ExecValueVariable` свойство «Передача заданий», сведения о передаче заданий могут быть сделаны доступными другим объектам в пакете. Дополнительные сведения см. в разделах [Переменные в службах Integration Services (SSIS)](../integration-services-ssis-variables.md) и [Использование переменных в пакетах](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Записи журнала  
 Задача «Передача заданий» позволяет настраивать запись в журнал следующих событий:  
  
-   TransferJobsTaskStarTransferringObjects   Эта запись журнала сообщает о начале передачи. В записях журнала указывается время запуска.  
  
-   TransferJobsTaskStarTransferringObjects   Эта запись журнала сообщает об окончании передачи. В записях журнала указывается время завершения.  
  
 Кроме того, запись журнала о событии `OnInformation` сообщает число переданных заданий, а запись журнала о событии `OnWarning` производится при перезаписи каждого задания, находящегося на сервере назначения.  
  
## <a name="security-and-permissions"></a>Безопасность и разрешения  
 Чтобы передавать задания, пользователь должен быть членом предопределенной роли сервера sysadmin или членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для базы данных msdb как в экземпляре-источнике, так и в экземпляре назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="configuration-of-the-transfer-jobs-task"></a>Настройка задачи «Передача заданий»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах.  
  
-   [Редактор задачи задания передача &#40;страница "Общие"&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Редактор задачи задания передача &#40;заданий страницы&#41;](../transfer-jobs-task-editor-jobs-page.md)  
  
-   [Страница "Выражения"](../expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств программным путем см. в следующих разделах:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
