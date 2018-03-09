---
title: "Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccf7f0b4eb9817aef38420111bb0ac2e7ce7bf2a
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Распределенные задания, шаги выполнения которых связаны с учетной записью-посредником, выполняются в контексте учетной записи-посредника на целевом сервере. При неудачной загрузке с главного сервера на целевой сервер шагов задания, использующего учетную запись-посредник, проверьте в столбце **error_message** таблицы **sysdownloadlist** базы данных **msdb** наличие следующих сообщений об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.»  
  
    Для устранения этой ошибки задайте для подраздела реестра **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***\<n*>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** значение **1 (true)**. По умолчанию для него задается значение **0** (**false**). Значение **MSSQL.**\<*n*> — имя экземпляра; например **MSSQL.1** или **MSSQL.3**.  
  
-   «Учетная запись-посредник не найдена.»  
  
    Чтобы устранить эту ошибку, убедитесь, что на целевом сервере существует учетная запись-посредник, имя которой совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>См. также:  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
  
