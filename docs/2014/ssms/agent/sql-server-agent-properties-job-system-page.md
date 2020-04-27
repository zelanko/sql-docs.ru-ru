---
title: Свойства агента SQL Server (страница "Система заданий") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8dceeba78e639ecbe2fd81fbdb1021293e75cf8a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63246085"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Свойства агента SQL Server (страница «Система заданий»)
  Эта страница используется для просмотра и изменения того, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как служба агента управляет заданиями.  
  
## <a name="options"></a>Параметры  
 **Время ожидания при завершении работы (в секундах)**  
 Указывает число секунд, в течение которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает завершения заданий при окончании работы. Если отведенное время истекло, а задание так и не завершилось, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принудительно его останавливает.  
  
 **Использовать неадминистративную учетную запись-посредник**  
 Задает неадминистративную учетную запись-посредник для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, поэтому этот [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр применим только при [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]управлении версиями агента до.  
  
 **User name**  
 Введите имя пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Пароль**  
 Введите пароль пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 **Поддомен**  
 Введите домен пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Реализация заданий](implement-jobs.md)  
  
  
