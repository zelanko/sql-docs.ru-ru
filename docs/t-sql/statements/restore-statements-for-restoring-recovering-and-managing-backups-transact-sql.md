---
title: Инструкции RESTORE для восстановления из копии, восстановления по журналу и управления резервными копиями (T-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 003f3adce58a228e4965f91c1104ff33b60b8398
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33701767"
---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>Инструкции RESTORE для восстановления из копии, восстановления по журналу и управления резервными копиями (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md.md )]

  В данном разделе описывается инструкция RESTORE для резервных копий. В дополнение к основной инструкции RESTORE {DATABASE | LOG} для восстановления резервных копий из копий и по журналу имеется несколько дополнительных инструкций RESTORE, которые помогут в управлении резервной копией и в планировании действий по восстановлению. Дополнительные команды RESTORE: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY и RESTORE VERIFYONLY.  
  
[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

> [!IMPORTANT]  
>  В предыдущих версиях SQL Server любой пользователь мог получить сведения о резервных наборах данных и устройствах резервного копирования с помощью инструкций Transact-SQL RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY и RESTORE VERIFYONLY. Поскольку эти инструкции предоставляют сведения о содержимом файлов резервных копий, для их выполнения в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях требуется разрешение CREATE DATABASE. Тем самым обеспечивается более надежная защита файлов резервных копий и данных, чем в предыдущих версиях. Дополнительные сведения об этом разрешении см. в разделе[ Разрешения базы данных GRANT (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|.|Description|  
|---------------|-----------------|  
|[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)|Описывает инструкции RESTORE DATABASE и RESTORE LOG языка Transact-SQL, используемые для восстановления базы данных из копии и по журналу из резервных копий, полученных с помощью команды BACKUP. Инструкция RESTORE DATABASE используется для баз данных во всех моделях восстановления. Инструкция RESTORE LOG используется только в модели полного восстановления и в модели восстановления с неполным протоколированием. Инструкция RESTORE DATABASE может также быть использована для возвращения базы данных к ее моментальному снимку.|  
|[Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Описаны аргументы, указанные в разделах "Синтаксис" для инструкции RESTORE и связанных с ней вспомогательных инструкций: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY и RESTORE VERIFYONLY. Большинство аргументов поддерживается только вложенными наборами этих шести инструкций. Поддержка каждого аргумента указана в его описании.|  
|[RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|Описывает инструкцию RESTORE FILELISTONLY языка Transact-SQL, которая используется для возврата результирующего набора, содержащего список баз данных и файлов журнала, содержащихся в резервном наборе данных.|  
|[RESTORE HEADERONLY (Transact-SQL)](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|Описывает инструкцию RESTORE HEADERONLY языка Transact-SQL, которая используется для возврата результирующего набора, содержащего все заголовочные сведения для всего набора резервных копий для заданного устройства резервного копирования.|  
|[RESTORE LABELONLY (Transact-SQL)](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|Описывает инструкцию RESTORE LABELONLY языка Transact-SQL, которая используется для возврата результирующего набора, содержащего сведения о среде резервного копирования, определенной для данного устройства резервного копирования.|  
|[RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|Описывает инструкцию языка RESTORE REWINDONLY Transact-SQL, которая используется для перемотки и закрытия ленточного устройства, которое осталось открытым после выполнения инструкций BACKUP или RESTORE с параметром NOREWIND.|  
|[RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|Описывает инструкцию RESTORE VERIFYONLY языка Transact-SQL, которая используется для проверки резервной копии, но не занимается ее восстановлением. Кроме этого, выполняется проверка завершенности резервного набора данных и читабельности копии. Структура данных не проверяется.|  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
