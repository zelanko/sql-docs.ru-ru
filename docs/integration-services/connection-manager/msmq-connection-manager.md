---
title: "Диспетчер соединений MSMQ | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: 0e028f9f648acc18d56dc05262adccbbc52f8f7e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="msmq-connection-manager"></a>диспетчер соединений MSMQ
  Диспетчер соединений MSMQ позволяет пакетам соединяться с очередями сообщений, которые используют службу очередей сообщений (также называемую MSMQ). Задача «Очередь сообщений», содержащаяся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует диспетчер соединений MSMQ.  
  
 При добавлении к пакету диспетчера MSMQ-сеансов службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который будет решать задачи MSMQ-сеансов во время работы, устанавливает свойства диспетчера соединений и добавляет его к коллекции **Connections** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **MSMQ**.  
  
 Настроить диспетчер соединений MSMQ можно следующими способами.  
  
-   Указать строку соединения.  
  
-   Указать путь к очереди сообщений для подключения.  
  
 Формат пути зависит от типа очереди, как показано в следующей таблице.  
  
|Тип очереди|Образец пути|  
|----------------|-----------------|  
|Открытый|\<Имя компьютера >\\< имя очереди\>|  
|Private|\<Имя компьютера > \Private$\\< имя очереди\>|  
  
 Для представления локального компьютера можно использовать знак точки («.»).  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Настройка диспетчера соединений MSMQ  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера MSMQ-сеансов](../../integration-services/connection-manager/msmq-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="msmq-connection-manager-editor"></a>редактор диспетчера MSMQ-сеансов
  Диалоговое окно **Диспетчер MSMQ-сеансов** используется для указания пути к очереди сообщений MSMQ.  
  
 Дополнительные сведения о диспетчере MSMQ-сеансов см. в разделе [MSMQ Connection Manager](../../integration-services/connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Диспетчер соединений MSMQ поддерживает локальные частные и общие очереди, а также удаленные общие очереди. Он не поддерживает удаленные частные очереди. Метод, обходящий это ограничение, использует задачу «Скрипт». Дополнительные сведения см. в разделе [Sending to a Remote Private Message Queue with the Script Task](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md).  
  
### <a name="options"></a>Параметры  
 **Название**  
 Задайте уникальное имя для диспетчера MSMQ-сеансов в рабочем процессе. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Description**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **Путь**  
 Введите полный путь очереди сообщений. Формат пути зависит от типа очереди.  
  
|Тип очереди|Образец пути|  
|----------------|-----------------|  
|Открытый|\<Имя компьютера >\\< имя очереди\>|  
|Private|\<Имя компьютера > \Private$\\< имя очереди\>|  
  
 Для представления локального компьютера можно использовать знак точки «.».  
  
 **Тест**  
 После настройки диспетчера MSMQ-сеансов убедитесь, что соединение работоспособно, нажав кнопку **Проверка**.  
  
## <a name="see-also"></a>См. также:  
 [Задача «Очередь сообщений»](../../integration-services/control-flow/message-queue-task.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
