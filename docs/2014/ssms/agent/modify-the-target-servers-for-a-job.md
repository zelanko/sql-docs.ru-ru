---
title: Изменение целевых серверов для задания | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5ab5397152adea4e5bd947adf4669f2214441dbb
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43807001"
---
# <a name="modify-the-target-servers-for-a-job"></a>Изменение целевых серверов для задания
  В этом разделе описывается изменение целевых серверов для заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для изменения целевых серверов для задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 По умолчанию данную хранимую процедуру могут выполнять члены предопределенной роли сервера sysadmin. Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента SQL Server в базе данных msdb.  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  SQLAgentOperatorRole  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Изменение целевых серверов для задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, **Задания**, затем щелкните правой кнопкой мыши задание и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Цели**, а затем выберите пункт **Выбрать локальный сервер в качестве целевого**или пункт **Выбрать несколько серверов в качестве целевых**.  
  
     При выборе пункта **Выбрать несколько серверов в качестве целевых**необходимо обозначить серверы, которые будут целевыми для задания, пометив флажки слева от имен соответствующих серверов. Убедитесь в том, что флажки серверов, которые не будут являться целевыми для задания, не помечены.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Изменение целевых серверов для задания  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере многосерверное задание Weekly Sales Backups назначается серверу SEATTLE2.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 Дополнительные сведения см. в разделе [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)  
  
  
