---
title: "Приложение sqlagent90 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "запуск агента SQL Server "
  - "sqlagent90, приложение"
  - "агент SQL Server, запуск"
  - "программы командной строки [SQL Server], sqlagent90"
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# Приложение sqlagent90
  Приложение **sqlagent90** запускает агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки. Обычно агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должен запускаться из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или с помощью методов SQL-DMO в приложении. Запускайте приложение **sqlagent90** из командной строки только, когда выполняется диагностика агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или если такое указание получено от основного поставщика поддержки.  
  
## Синтаксис  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## Аргументы  
 **-c**  
 Указывает, что агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запускается из командной строки и не зависит от диспетчера управления службами Microsoft Windows. При использовании параметра **-c** агентом [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] нельзя управлять с помощью оснастки "Службы" в элементе "Администрирование" панели управления и из диспетчера конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Этот аргумент является обязательным.  
  
 **-v**  
 Указывает, что агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работает в подробном режиме и производит запись диагностических данных в окно командной строки. Диагностические данные — это те же данные, которые записываются в журнал ошибок агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **-i** *instance_name*  
 Указывает, что агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] подключается к именованному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], определенному аргументом *имя_экземпляра*.  
  
## Замечания  
 После отображения сообщения с указанием авторских прав приложение **sqlagent90** отображает выводимые данные в окне командной строки, только если указан параметр **-v**. Чтобы остановить работу приложения **sqlagent90**, нажмите клавиши CTRL+C в командной строке. Не закрывайте окно командной строки перед остановкой работы приложения **sqlagent90**.  
  
## См. также:  
 [Задачи автоматизированного администрирования (агент SQL Server)](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  