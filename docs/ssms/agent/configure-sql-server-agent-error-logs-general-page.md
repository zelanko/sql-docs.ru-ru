---
title: Журналы ошибок конфигурации агента SQL Server (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d9feb892096bd620f817c0ae8c913fa2eaf3416c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707242"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Журналы ошибок конфигурации агента SQL Server (страница «Общие»)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница используется для просмотра и изменения параметров журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
**Файл журнала ошибок**  
Указывает файл, в который агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит запись журнала ошибок.  
  
**...**  
Перейдите к файлу журнала ошибок.  
  
**Запись журнала ошибок в OEM**  
Запись файла журнала ошибок производится не в Юникоде. Это позволяет уменьшить место на диске, необходимое для файла журнала. Однако при включении этого параметра могут возникнуть трудности с чтением сообщений, содержащих данные в Юникоде.  
  
**ошибки**  
В файл журнала ошибок производится только запись ошибок и информационных сообщений.  
  
**Предупреждения**  
В файл журнала ошибок производится только запись предупреждений и информационных сообщений.  
  
**Сведения**  
В файл журнала ошибок производится только запись информационных сообщений.  
  
## <a name="see-also"></a>См. также:  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
