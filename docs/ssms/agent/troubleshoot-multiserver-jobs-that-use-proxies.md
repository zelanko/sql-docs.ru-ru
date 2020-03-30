---
title: Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e3b579bb9154b59247b500c921850cae4e989d39
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75257852"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Распределенные задания, шаги выполнения которых связаны с учетной записью-посредником, выполняются в контексте учетной записи-посредника на целевом сервере. При неудачной загрузке с главного сервера на целевой сервер шагов задания, использующего учетную запись-посредник, проверьте в столбце **error_message** таблицы **sysdownloadlist** базы данных **msdb** наличие следующих сообщений об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.»  
  
    Для устранения этой ошибки задайте для подраздела реестра **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.** _\<n\>_ **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** значение **1 (true)** . По умолчанию для него задается значение **0** (**false**). Значение **MSSQL.** \<*n*> — имя экземпляра; например **MSSQL.1** или **MSSQL.3**.  
  
-   «Учетная запись-посредник не найдена.»  
  
    Чтобы устранить эту ошибку, убедитесь, что на целевом сервере существует учетная запись-посредник, имя которой совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>См. также:  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
  
