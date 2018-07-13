---
title: Просмотр журнала ошибок SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b052500749f5e1ea6c4bcc22b5fc76da2e3407a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218434"
---
# <a name="viewing-the-sql-server-error-log"></a>Просмотр журнала ошибок SQL Server
  Журнал ошибок сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет убедиться, что процессы были завершены успешно (например, операции резервного копирования и восстановления, пакеты команд или другие скрипты и процессы). Это полезно при определении любых текущих или потенциальных проблем, включая сообщения автоматического восстановления (особенно если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был остановлен и перезапущен), сообщения ядра и другие сообщения об ошибках на уровне сервера.  
  
 Журнал ошибок сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно просмотреть, используя среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или любой текстовый редактор. Дополнительные сведения о просмотре журнала ошибок см. в разделе [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md). По умолчанию журнал ошибок содержится в файлах `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` и `ERRORLOG.`*n* .  
  
 Новый журнал ошибок создается при каждом запуске экземпляра сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , хотя циклическую смену журнала ошибок можно организовать при помощи системной хранимой процедуры [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) без перезапуска экземпляра сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обычно сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит резервные копии шести предыдущих журналов и присваивает наиболее свежей копии расширение «.1», следующей расширение «.2» и т. д. Файл текущего журнала ошибок расширения не имеет.  
  
 Помните, что журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно также просматривать на экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые находятся вне сети или не запускаются. Дополнительные сведения см. в разделе [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md).  
  
  
