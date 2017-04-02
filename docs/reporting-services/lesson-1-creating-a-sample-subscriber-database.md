---
title: "Занятие&#160;1. Создание образца базы данных подписчика | Microsoft Docs"
ms.custom: ""
ms.date: "05/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Занятие&#160;1. Создание образца базы данных подписчика
На этом занятии учебника [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] создается небольшая база данных подписчика для хранения данных подписки, которые будут использоваться управляемой данными подпиской. После обработки подписки сервер отчетов получит эти данные и использует их для настройки выходных данных отчетов. Например, строки данных включают номера заказов, используемые для фильтров, и сведения о том, в каком формате будут создаваться отчеты.  
  
На этом занятии предполагается, что для создания базы данных [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] используется среда [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)].  
  
### Создание образца базы данных подписчика  
  
1.  Запустите среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] и установите соединение с экземпляром [!INCLUDE[ssDEnoversion_md](../includes/ssdenoversion-md.md)].  
  
2.  Щелкните правой кнопкой мыши "Базы данных" и выберите команду **Создать базу данных...**  
  
3.  В диалоговом окне "Создать базу данных" в поле **Имя базы данных** введите *Подписчики*. 
4. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Нажмите кнопку **Создать запрос** на панели инструментов.  
  
6.  Скопируйте следующие инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] в пустой запрос:  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
7.  Нажмите кнопку **! Выполнить** на панели инструментов.  
  
8.  С помощью инструкции SELECT удостоверьтесь, что создано три строки данных. Например: `select * from OrderInfo`  
  
## Следующие шаги  
+ Успешно завершено создание данных подписки, которые будут управлять распространением отчетов и изменять выходные данные отчетов в соответствии с параметрами настройки для каждого из подписчиков. 
+ Далее предстоит изменить свойства источника данных отчета так, чтобы использовались хранимые учетные данные. 
+ Вы также измените конструкцию отчета, включив в нее параметр, который будет использоваться подпиской с данными подписчика. [Занятие 2. Изменение свойств источника данных отчета](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md).  
  
## См. также:  
[Создание управляемой данными подписки (учебник по службам SSRS)](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
[Создание базы данных](../relational-databases/databases/create-a-database.md)  
[Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  
  
  
