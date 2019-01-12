---
title: Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e3c3991bd4732d542bf1ce79e83000e738ff77
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100039"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники
  Распределенные задания, шаги выполнения которых связаны с учетной записью-посредником, выполняются в контексте учетной записи-посредника на целевом сервере. При неудачной загрузке с главного сервера на целевой сервер шагов задания, использующего учетную запись-посредник, проверьте в столбце **error_message** таблицы **sysdownloadlist** базы данных **msdb** наличие следующих сообщений об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.»  
  
     Для устранения этой ошибки задайте для подраздела реестра **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.**_\<n_>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** значение **1 (true)**. По умолчанию имеет значение этого подраздела **0** (`false`). Значение **MSSQL.**\<*n*> — имя экземпляра; например **MSSQL.1** или **MSSQL.3**.  
  
-   «Учетная запись-посредник не найдена.»  
  
     Чтобы устранить эту ошибку, убедитесь, что на целевом сервере существует учетная запись-посредник, имя которой совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Создание многосерверной среды](create-a-multiserver-environment.md)  
  
  
