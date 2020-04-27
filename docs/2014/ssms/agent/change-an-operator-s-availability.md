---
title: Изменение доступности оператора | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- reactivating operators
- removing operators
- deleting operators
- available operators [SQL Server]
- dropping operators
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- disabling operators
- operators (users) [Database Engine], changing availability with Management Studio
ms.assetid: 10d58b92-b67b-47e2-af9c-9f9fd6968bba
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 11e5b26a9e2a953aff319b41749d2c12be1a880e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63017098"
---
# <a name="change-an-operator39s-availability"></a>Изменение доступности оператора
  В этом разделе описано, как изменить расписание оператора по приему уведомлений о предупреждениях в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Изменение доступности оператора с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Изменять данные операторов могут указывать только члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-an-operators-availability"></a>Изменение доступности оператора  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий оператора, которого нужно включить или отключить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните значок «плюс», чтобы развернуть папку **Операторы** .  
  
4.  Щелкните правой кнопкой мыши оператора, которого нужно включить или отключить, и выберите пункт **Свойства**, а затем перейдите на вкладку **Общие** .  
  
5.  В диалоговом окне**свойства** _operator_name_установите или снимите флажок **включено** .  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-change-an-operators-availability"></a>Изменение доступности оператора  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- disables the 'Fran??ois Ajenstat' operator  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 0;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).  
  
  
