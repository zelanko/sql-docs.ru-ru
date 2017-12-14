---
title: "Свойства агента SQL Server (страница \"Система заданий\") | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ba6041cd4169bd8c87fbf1e220d91a86ed2fdd1
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-properties-job-system-page"></a>Свойства агента SQL Server (страница «Система заданий»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Эта страница предназначена для просмотра и изменения того, каким образом служба агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] управляет заданиями.  
  
## <a name="options"></a>Параметры  
**Время ожидания при завершении работы (в секундах)**  
Указывает число секунд, в течение которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ожидает завершения заданий при окончании работы. Если отведенное время истекло, а задание так и не завершилось, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] принудительно его останавливает.  
  
**Использовать неадминистративную учетную запись-посредник**  
Задает неадминистративную учетную запись-посредник для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Имя пользователя**  
Введите имя пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Пароль**  
Введите пароль пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)].  
  
**Домен**  
Введите домен пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
  
