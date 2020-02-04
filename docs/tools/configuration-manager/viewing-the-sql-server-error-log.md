---
title: Просмотр журнала ошибок SQL Server
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 421836f23129879670dd4ff2194c553adaeaa12b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307575"
---
# <a name="viewing-the-sql-server-error-log"></a>Просмотр журнала ошибок SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Журнал ошибок сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет убедиться, что процессы были завершены успешно (например, операции резервного копирования и восстановления, пакеты команд или другие скрипты и процессы). Это полезно при определении любых текущих или потенциальных проблем, включая сообщения автоматического восстановления (особенно если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был остановлен и перезапущен), сообщения ядра и другие сообщения об ошибках на уровне сервера.  
  
 Журнал ошибок сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно просмотреть, используя среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или любой текстовый редактор. Дополнительные сведения о просмотре журнала ошибок см. в разделе [Open Log File Viewer](../../relational-databases/logs/open-log-file-viewer.md). По умолчанию журнал ошибок содержится в файлах `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` и `ERRORLOG.`*n* .  
  
 Новый журнал ошибок создается при каждом запуске экземпляра сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , хотя циклическую смену журнала ошибок можно организовать при помощи системной хранимой процедуры [sp_cycle_errorlog](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md) без перезапуска экземпляра сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обычно сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит резервные копии шести предыдущих журналов и присваивает наиболее свежей копии расширение «.1», следующей расширение «.2» и т. д. Файл текущего журнала ошибок расширения не имеет.  
  
 Помните, что журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно также просматривать на экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые находятся вне сети или не запускаются. Дополнительные сведения см. в разделе [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md).  
  
  
