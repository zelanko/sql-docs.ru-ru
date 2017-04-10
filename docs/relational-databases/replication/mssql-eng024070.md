---
title: "MSSQL_ENG024070 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG024070, ошибка"
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG024070
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|24070|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Клиент не располагает требуемыми правами доступа.|  
  
## Объяснение  
 Это общая ошибка, которая может возникнуть независимо от того, реплицируется база данных или нет. Для сервера в топологии репликации эта ошибка обычно означает, что учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была изменена с использованием диспетчера управления службами [!INCLUDE[msCoName](../../includes/msconame-md.md)] , а не с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если попытаться выполнить задание агента после изменения учетной записи службы, выполнение задания может закончится выдачей примерно следующего сообщения об ошибке:  
  
 «Выполняется от имени: \< Имя_учетной_записи>. Репликация — Подсистема моментальных снимков: агента \< ИмяАгента> сбой. Выполняется от имени: \< Имя_учетной_записи>. Клиент не располагает требуемыми правами доступа. Шаг завершился с ошибкой. [SQLSTATE 42000] (Ошибка 14151). Шаг завершился с ошибкой».  
  
 Эта проблема возникает из-за того, что диспетчер управления службами Windows не может предоставить новой учетной записи службы для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуемые разрешения.  
  
## Действие пользователя  
 Чтобы в дальнейшем избежать появления этой проблемы, при изменении учетных записей служб и паролей всегда пользуйтесь диспетчером конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а не диспетчером управления службами Windows.  
  
 Чтобы устранить эту проблему, при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] смените учетную запись службы обратно на исходную. Затем при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перейдите на новую учетную запись. При этом диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] добавляет новую учетную запись в следующую группу безопасности:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Членство в ней предоставляет новой учетной записи разрешения, необходимые для выполнения задания агента репликации.  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Управление именами входа и паролями в репликации](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  