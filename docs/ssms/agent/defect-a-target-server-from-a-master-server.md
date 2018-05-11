---
title: Отключение целевого сервера от главного | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: df10e43d1b039fbc9bd7a56a66ace4cc2eba1741
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного сервера
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается исключение целевого сервера из главного в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] или управляющих объектов SQL Server (SMO). Запустите эту процедуру на целевом сервере.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для исключения целевого сервера используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
    [SMO](#PowerShellProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного  
  
1.  В **обозревателе объектов**разверните сервер, настроенный как целевой сервер.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server**, выберите **Администрирование нескольких серверов**и нажмите **Отключить**.  
  
3.  Щелкните **Да** , подтверждая, что этот целевой сервер необходимо отключить от главного сервера.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
```  
sp_msx_defect ;  
```  
  
Дополнительные сведения см. в разделе [sp_msx_defect (Transact-SQL)](http://msdn.microsoft.com/en-us/0dfd963a-3bc5-4b58-94f7-aec976da2883).  
  
## <a name="PowerShellProcedure"></a>Использование управляющих объектов SQL Server (SMO)  
Используйте **метод MsxDefect**.  
  
## <a name="see-also"></a>См. также:  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Отключение нескольких целевых серверов от главного](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
