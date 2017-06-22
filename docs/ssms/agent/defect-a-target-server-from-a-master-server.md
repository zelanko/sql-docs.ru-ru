---
title: "Отключение целевого сервера от главного | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 660fbd83ba89ceb38ca240fe2c8c7d2d6d6b8dcd
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного
В этом разделе описывается исключение целевого сервера из главного в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] или управляющих объектов SQL Server (SMO). Запустите эту процедуру на целевом сервере.  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [безопасность](#Security)  
  
-   **Для исключения целевого сервера используется:**  
  
    [Среда Среда SQL Server Management Studio](#SSMSProcedure)  
  
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
  

