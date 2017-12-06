---
title: "SQL Server Integration Services свойства (вход в систему) | Документы Microsoft"
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
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1eaab42d630f5952bf93835d8c3bcd568552a468
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>Свойства служб SQL Server Integration Services (вкладка «Вход в систему»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Используйте **вход в систему** вкладке [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **свойства** для указания учетной записи, используемой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , а также для запуска и остановки службы.  
  
## <a name="options"></a>Параметры  
 **Локальная системная учетная запись**  
 Укажите локальную системную учетную запись, для которой не требуется пароль. Однако локальная системная учетная запись может ограничить взаимодействие служб с другими серверами, это зависит от прав доступа, предоставленных этой учетной записи.  
  
 **Эта учетная запись**  
 Укажите локальную или доменную учетную запись пользователя, использующую проверку подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует использовать доменную учетную запись пользователя с минимальными правами. Дополнительные сведения о выборе учетной записи см. в разделе «Настройка учетных записей служб Windows» электронной документации.  
  
 **Имя учетной записи**  
 Укажите имя локальной или доменной учетной записи.  
  
 **Пароль**  
 Введите пароль для учетной записи.  
  
 **Подтверждение пароля**  
 Введите пароль для учетной записи еще раз.  
  
 **Запуск**  
 Запускает службу.  
  
 **Остановить**  
 Остановить службу.  
  
 **Приостановить**  
 Приостановить службу.  
  
 **Возобновить**  
 Возобновить приостановленную работу службы.  
  
  
