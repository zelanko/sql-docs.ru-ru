---
title: "SQL Server Integration Services (вкладка «службы») свойства | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac5eaaf1b4b5edf484e1dd98106b9c1b32056468
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-integration-services-properties-service-tab"></a>Свойства служб SQL Server Integration Services (вкладка «Служба»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Используйте **службы**на вкладке [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **свойства** диалогового окна для просмотра или указания следующих параметров.  
  
## <a name="options"></a>Параметры  
 **Путь к двоичным файлам**  
 Отображает расположение программных файлов, используемых этой службой.  
  
 **Контроль ошибок**  
 1 означает `SERVICE_ERROR_NORMAL`. Если службе не удалось запуститься при запуске компьютера, программа запуска заносит в журнал сообщение об ошибке и выдает всплывающее сообщение об ошибке, но продолжает выполнять операцию запуска. Это значение невозможно изменить.  
  
 **Код завершения**  
 Код ошибки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows определяет любые проблемы, возникшие при запуске или остановке службы. Этому свойству присваивается значение **ERROR_SERVICE_SPECIFIC_ERROR** (1066), если ошибка является уникальной для службы, представленной этим классом, а сведения об ошибке доступны в свойстве **ServiceSpecificExitCode** . Во время выполнения и после нормального завершения работы служба присваивает этому параметру значение NO_ERROR (0).  
  
 **Host Name**  
 Отображает имя компьютера или кластера, где запущена служба [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Название**  
 Указывает отображаемое имя службы.  
  
 **Идентификатор процесса**  
 Отображает идентификатор процесса Windows.  
  
 **Тип службы SQL**  
 Отображает тип службы, предоставленной для вызывающих процессов. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает несколько служб.  
  
 **Режим запуска**  
 Установите для этой службы один из следующих вариантов:  
  
-   Вручную. Эта служба не запускается автоматически при запуске компьютера. Необходимо запустить службу при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другого средства.  
  
-   Автоматически. Эта служба пытается запуститься при запуске компьютера.  
  
-   Отключено. Служба не может быть запущена.  
  
 **Состояние**  
 Указывает, была ли служба запущена, остановлена или отключена. «**…**» указывает, что ожидается изменение состояния.  
  
  
