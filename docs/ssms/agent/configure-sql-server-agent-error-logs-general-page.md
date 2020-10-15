---
description: Журналы ошибок конфигурации агента SQL Server (страница «Общие»)
title: Настройка журналов ошибок (страница "Общие")
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 85477939fcc055e09177e0dbf3d0db2667be2c4f
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035673"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Журналы ошибок конфигурации агента SQL Server (страница «Общие»)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

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
  
**Информация**  
В файл журнала ошибок производится только запись информационных сообщений.  
  
## <a name="see-also"></a>См. также:  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
