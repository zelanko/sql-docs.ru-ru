---
title: "Свойства агента SQL Server (вкладка «службы») | Документы Microsoft"
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
ms.assetid: 452857fb-be1b-4e1e-851c-dd2216640f35
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 992dc10e54ca038898388052067b4c26d248e257
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-properties-service-tab"></a>Свойства агента SQL Server (вкладка «Службы»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Эта служба является [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы агента. Значения свойств, окрашенные в светло-серый цвет, нельзя изменить при помощи этого приложения.  
  
## <a name="options"></a>Параметры  
 **Путь к двоичным файлам**  
 Отображает расположение программных файлов, используемых этой службой.  
  
 **Контроль ошибок**  
 1 означает `SERVICE_ERROR_NORMAL`. Если службе не удалось запуститься при запуске компьютера, программа запуска заносит в журнал сообщение об ошибке и выдает всплывающее сообщение об ошибке, но продолжает выполнять операцию запуска. Это значение невозможно изменить.  
  
 **Код завершения**  
 При возникновении ошибки ее номер выводится в этом окне. Этот номер обеспечивает возможность устранения ошибок, используйте его для поиска в базе знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] или сообщите его службе технической поддержки.  
  
 **Host Name**  
 Отображает имя компьютера или кластера, где запущен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Название**  
 Указывает отображаемое имя службы.  
  
 **Идентификатор процесса**  
 Отображает идентификатор процесса [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Тип службы SQL**  
 Отображает тип службы, предоставленной для вызывающих процессов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает несколько служб.  
  
 **Режим запуска**  
 Установите для этой службы один из следующих вариантов:  
  
-   Вручную. Эта служба не запускается автоматически при запуске компьютера. Необходимо запустить службу при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другого средства.  
  
-   Автоматически. Эта служба пытается запуститься при запуске компьютера.  
  
-   Отключено. Служба не может быть запущена.  
  
 **Состояние**  
 Указывает, была ли служба запущена, остановлена или отключена. «**…**» указывает, что ожидается изменение состояния.  
  
  
