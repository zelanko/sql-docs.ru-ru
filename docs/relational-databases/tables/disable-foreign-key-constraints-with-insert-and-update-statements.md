---
title: "Отключение ограничений внешнего ключа для инструкций INSERT и UPDATE | Microsoft Docs"
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
  - "ограничения [SQL Server], внешние ключи"
  - "внешние ключи [SQL Server], отключение ограничений"
  - "отключение ограничений"
  - "инструкция UPDATE [SQL Server], ограничения по внешнему ключу"
  - "инструкция INSERT [SQL Server], ограничения по внешнему ключу"
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Отключение ограничений внешнего ключа для инструкций INSERT и UPDATE
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ограничение внешнего ключа можно отключить в транзакциях INSERT и UPDATE с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Используйте эту возможность, если новые данные будут нарушать существующее ограничение или если ограничение относится только к данным, уже помещенным в базу данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Отключение ограничений внешнего ключа для инструкций INSERT и UPDATE с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 После отключения этих ограничений будущие вставки и обновления столбца не проверяются по проверочным ограничениям.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Отключение ограничений внешнего ключа для инструкций INSERT и UPDATE  
  
1.  Разверните в **обозревателе объектов**таблицу с ограничением, затем разверните папку **Ключи** .  
  
2.  Щелкните правой кнопкой мыши ограничение и выберите команду **Изменить**.  
  
3.  В сетке под **конструктором таблиц** щелкните пункт **Принудительное использование ограничения внешнего ключа** и выберите значение **Нет** в раскрывающемся списке.  
  
4.  Щелкните **Закрыть**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Отключение ограничений внешнего ключа для инструкций INSERT и UPDATE  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующие примеры в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  