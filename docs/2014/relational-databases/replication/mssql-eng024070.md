---
title: MSSQL_ENG024070 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2f5fc8fdc9b522ad79e67a7769ba2571b7a80af9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54123474"
---
# <a name="mssqleng024070"></a>MSSQL_ENG024070
    
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
  
 «Выполняется от имени: \<Учетная_запись_пользователя >. Подсистема моментальных снимков репликации репликации: агент \<Имя_агента > не удалось. Выполняется от имени: \<Учетная_запись_пользователя >. Клиент не располагает требуемыми правами доступа. Шаг завершился с ошибкой. `[SQLSTATE 42000] (Error 14151)`. Шаг завершился с ошибкой».  
  
 Эта проблема возникает из-за того, что диспетчер управления службами Windows не может предоставить новой учетной записи службы для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуемые разрешения.  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы в дальнейшем избежать появления этой проблемы, при изменении учетных записей служб и паролей всегда пользуйтесь диспетчером конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а не диспетчером управления службами Windows.  
  
 Чтобы устранить эту проблему, при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] смените учетную запись службы обратно на исходную. Затем при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перейдите на новую учетную запись. При этом диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] добавляет новую учетную запись в следующую группу безопасности:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Членство в ней предоставляет новой учетной записи разрешения, необходимые для выполнения задания агента репликации.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)   
 [Управление именами для входа и паролями при репликации](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Диспетчер конфигурации SQL Server](../sql-server-configuration-manager.md)  
  
  
