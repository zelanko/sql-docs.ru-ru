---
title: Занятие 1. Создание образца базы данных подписчика | Документы Майкрософт
description: Узнайте, как создать небольшую базу данных подписчика для хранения данных подписки, которые будут использоваться управляемой данными подпиской.
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a62e0e1c47cd6df4d2d5e4f28b35294af694a824
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243275"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a>Урок 1. Создание образца базы данных подписчика

На этом занятии учебника [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] создается небольшая база данных подписчика для хранения данных подписки, которые будут использоваться управляемой данными подпиской. После обработки подписки сервер отчетов получит эти данные и использует их для настройки выходных данных отчетов. Например, строки данных включают номера заказов, используемые для фильтров, и сведения о том, в каком формате будут создаваться отчеты.  
  
На этом занятии предполагается, что для создания базы данных SQL Server используется среда [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)].  
  
### <a name="to-create-a-sample-subscriber-database"></a>Создание образца базы данных подписчика  
  
1.  Запустите среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]и установите соединение с экземпляром [!INCLUDE[ssDEnoversion_md](../includes/ssdenoversion-md.md)].  
  
2.  Щелкните правой кнопкой мыши "Базы данных" и выберите команду **Создать базу данных...**  
  
3.  В диалоговом окне "Создать базу данных" в поле **Имя базы данных**введите *Подписчики*. 
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
  
7.  Щелкните **! Выполнить** на панели инструментов.  
  
8.  С помощью инструкции SELECT удостоверьтесь, что создано три строки данных. Например: `select * from OrderInfo`  
  
## <a name="next-steps"></a>Next Steps  
+ Успешно завершено создание данных подписки, которые будут управлять распространением отчетов и изменять выходные данные отчетов в соответствии с параметрами настройки для каждого из подписчиков. 
+ Далее предстоит изменить свойства источника данных отчета так, чтобы использовались хранимые учетные данные. 
+ Вы также измените конструкцию отчета, включив в нее параметр, который будет использоваться подпиской с данными подписчика. [Занятие 2. Изменение свойств источника данных отчета](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md).  

## <a name="next-steps"></a>Дальнейшие действия

[Создание управляемой данными подписки](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
[Создание базы данных](../relational-databases/databases/create-a-database.md)  
[Создание простого табличного отчета](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
