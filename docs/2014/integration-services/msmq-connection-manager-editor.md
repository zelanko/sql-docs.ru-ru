---
title: Редактор диспетчера подключений MSMQ | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 91b448a87408a830464b50f641e6eefa8cf3f12c
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66057643"
---
# <a name="msmq-connection-manager-editor"></a>редактор диспетчера MSMQ-сеансов
  Диалоговое окно **Диспетчер MSMQ-сеансов** используется для указания пути к очереди сообщений MSMQ.  
  
 Дополнительные сведения о диспетчере MSMQ-сеансов см. в разделе [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Диспетчер соединений MSMQ поддерживает локальные частные и общие очереди, а также удаленные общие очереди. Он не поддерживает удаленные частные очереди. Метод, обходящий это ограничение, использует задачу «Скрипт». Дополнительные сведения см. в разделе [Отправка в удаленную закрытую очередь сообщений в задаче «Скрипт»](control-flow/script-task.md).  
  
## <a name="options"></a>Параметры  
 **Name**  
 Задайте уникальное имя для диспетчера MSMQ-сеансов в рабочем процессе. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Описание**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **Путь**  
 Введите полный путь очереди сообщений. Формат пути зависит от типа очереди.  
  
|Тип очереди|Образец пути|  
|----------------|-----------------|  
|Открытый|\<имя компьютера>\\<имя очереди\>|  
|Private|\<имя компьютера>\Private$\\<имя очереди\>|  
  
 Для представления локального компьютера можно использовать знак точки «.».  
  
 **Тест**  
 После настройки диспетчера MSMQ-сеансов убедитесь, что соединение работоспособно, нажав кнопку **Проверка**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
