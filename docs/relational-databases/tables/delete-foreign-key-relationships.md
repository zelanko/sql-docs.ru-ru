---
title: "Удаление связей по внешнему ключу | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "внешние ключи [SQL Server], удаление"
  - "исключение внешних ключей"
  - "удаление внешних ключей"
ms.assetid: 9c9e9ae4-9e03-4137-acb6-b18928a0c4ca
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Удаление связей по внешнему ключу
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Можно удалить ограничение внешнего ключа в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. При удалении ограничения внешнего ключа удаляется требование принудительного создания ссылочной целостности.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Удаление ограничения внешнего ключа при помощи различных средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Удаление ограничения внешнего ключа  
  
1.  Разверните в **обозревателе объектов**таблицу с ограничением, после чего разверните узел **Ключи**.  
  
2.  Щелкните правой кнопкой мыши ограничение и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Удаление ограничения внешнего ключа  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.DocExe   
    DROP CONSTRAINT FK_Column_B;   
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
  