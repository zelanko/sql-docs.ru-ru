---
title: Контроль за журналом ошибок | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: configuration-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af83c65a76d5dc190ca8833f247d3bc5e3138505
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="monitoring-the-error-logs"></a>Контроль за журналом ошибок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заносит сведения об определенных событиях системы и пользовательских операциях в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Оба журнала автоматически фиксируют отметки времени всех зарегистрированных событий. Сведения из журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются для устранения неполадок, связанных с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Журнал приложений Windows предоставляет общую картину событий, произошедших в операционной системе Windows, а также всех событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для просмотра журнала приложений Windows и фильтрации сведений используется программа просмотра событий Windows. Например, можно отфильтровать такие события, как сведения, предупреждения, ошибки, успешный аудит и неуспешный аудит.  
  
## <a name="comparing-error-and-application-log-output"></a>сравнение содержимого журнала ошибок и приложений  
 Чтобы определить причину проблемы, можно использовать как журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и журнал приложений Windows. Например, в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут встречаться сообщения, не несущие в себе сведений о причине проблемы. Сравнивая даты и время событий в этих журналах, можно сузить список потенциальных причин. Программа просмотра файла журнала среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет объединить журналы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows в общий список, облегчая понимание событий, связанных с сервером и событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе «Средство просмотра журнала» электронной документации по SQL Server.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Просмотр журнала ошибок SQL Server](../../tools/configuration-manager/viewing-the-sql-server-error-log.md)|Содержит сведения о журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и способах его просмотра.|  
|[Просмотр журнала приложений Windows](../../tools/configuration-manager/viewing-the-windows-application-log.md)|Содержит сведения о журнале приложений Windows и способах его просмотра.|  
  
  
