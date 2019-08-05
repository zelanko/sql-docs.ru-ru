---
title: MSSQL_ENG024070 | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: c45c23cd93cfda524f9987ae8b2181aece99f9fa
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770289"
---
# <a name="mssqleng024070"></a>MSSQL_ENG024070
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|24070|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Клиент не располагает требуемыми правами доступа.|  
  
## <a name="explanation"></a>Объяснение  
 Это общая ошибка, которая может возникнуть независимо от того, реплицируется база данных или нет. Для сервера в топологии репликации эта ошибка обычно означает, что учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была изменена с использованием диспетчера управления службами [!INCLUDE[msCoName](../../includes/msconame-md.md)] , а не с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если попытаться выполнить задание агента после изменения учетной записи службы, выполнение задания может закончится выдачей примерно следующего сообщения об ошибке:  
  
 `Executed as user: \<UserAccount>. Replication-Replication Snapshot Subsystem: agent \<AgentName> failed. Executed as user: \<UserAccount>. A required privilege is not held by the client. The step failed. [SQLSTATE 42000] (Error 14151). The step failed.`  
  
 Эта проблема возникает из-за того, что диспетчер управления службами Windows не может предоставить новой учетной записи службы для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуемые разрешения.  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы в дальнейшем избежать появления этой проблемы, при изменении учетных записей служб и паролей всегда пользуйтесь диспетчером конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а не диспетчером управления службами Windows.  
  
 Чтобы устранить эту проблему, при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] смените учетную запись службы обратно на исходную. Затем при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перейдите на новую учетную запись. При этом диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] добавляет новую учетную запись в следующую группу безопасности:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Членство в ней предоставляет новой учетной записи разрешения, необходимые для выполнения задания агента репликации.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Управление именами для входа и паролями при репликации](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
