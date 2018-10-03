---
title: Свойства агента SQL Server (страница "Система заданий") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8f8f99faf04c392fbb7a2a11c30b42db4d40d6df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062040"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Свойства агента SQL Server (страница «Система заданий»)
  Эта страница предназначена для просмотра и изменения того, каким образом служба агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляет заданиями.  
  
## <a name="options"></a>Параметры  
 **Время ожидания при завершении работы (в секундах)**  
 Указывает число секунд, в течение которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает завершения заданий при окончании работы. Если отведенное время истекло, а задание так и не завершилось, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принудительно его останавливает.  
  
 **Использовать неадминистративную учетную запись-посредник**  
 Задает неадминистративную учетную запись-посредник для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Имя пользователя**  
 Введите имя пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Пароль**  
 Введите пароль пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии поддерживают несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 **Домен**  
 Введите домен пользователя для неадминистративной учетной записи-посредника. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько учетных записей-посредников, и поэтому этот параметр применим только в случае работы с версиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Реализация заданий](implement-jobs.md)  
  
  
