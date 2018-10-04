---
title: Диспетчер подключений MSMQ | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a1501af4a26c0e039df3113a719a61e1e2c3f40a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135044"
---
# <a name="msmq-connection-manager"></a>диспетчер соединений MSMQ
  Диспетчер соединений MSMQ позволяет пакетам соединяться с очередями сообщений, которые используют службу очередей сообщений (также называемую MSMQ). Задача «Очередь сообщений», содержащаяся в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует диспетчер соединений MSMQ.  
  
 При добавлении к пакету диспетчер соединений MSMQ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер, который будет решать задачи соединений MSMQ во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений для соединений `Connections` коллекции пакет. `ConnectionManagerType` Свойства диспетчера соединений присваивается `MSMQ`.  
  
 Настроить диспетчер соединений MSMQ можно следующими способами.  
  
-   Указать строку соединения.  
  
-   Указать путь к очереди сообщений для подключения.  
  
 Формат пути зависит от типа очереди, как показано в следующей таблице.  
  
|Тип очереди|Образец пути|  
|----------------|-----------------|  
|Открытый|\<имя компьютера>\\<имя очереди\>|  
|Private|\<имя компьютера>\Private$\\<имя очереди\>|  
  
 Для представления локального компьютера можно использовать знак точки («.»).  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Настройка диспетчера соединений MSMQ  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера MSMQ-сеансов](../msmq-connection-manager-editor.md).  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Задача «Очередь сообщений»](../control-flow/message-queue-task.md)   
 [Службы Integration Services &#40;SSIS&#41; подключений](integration-services-ssis-connections.md)  
  
  
