---
title: "Подключение к редактору запросов | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6fcc396dc778bdf05e2ccc701be5e032ffc4ed69
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-2-1---connecting-with-query-editor"></a>Занятие 2–1. Подключение к редактору запросов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет создавать или редактировать код без соединения с сервером. Это может оказаться полезным в том случае, если сервер недоступен или требуется экономить ограниченные ресурсы сервера или сети. Можно заменить соединение с редактором запросов на соединение с новым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не открывая нового окна редактора запросов и не вводя код повторно.  
  
## <a name="coding-offline"></a>Программирование в режиме «вне сети»  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a>Написание программы в режиме «вне сети» с последующим подключением к различным серверам  
  
1.  На панели инструментов среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] нажмите кнопку **Запрос к ядру СУБД** , чтобы открыть редактор запросов.  
  
2.  В диалоговом окне **Подключиться к компоненту Database Engine** нажмите кнопку **Отмена**. Будет открыт редактор запросов, в строке заголовка которого будет указано, что соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]не установлено.  
  
3.  В панели кода введите следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
    На этом этапе можно подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выбрав команды **Подключиться**, **Выполнить**, **Выполнить анализ**или **Показать предполагаемый план выполнения**, которые доступны в меню **Запрос** , на панели инструментов редактора запросов или в контекстном меню, открывающемся при щелчке правой кнопкой мыши в окне редактора запросов. В этом практическом занятии будет использована панель инструментов.  
  
4.  На панели инструментов нажмите кнопку **Выполнить** , чтобы открыть диалоговое окно **Подключиться к компоненту Database Engine** .  
  
5.  В текстовом поле **Имя сервера** введите имя сервера, а затем нажмите кнопку **Параметры**.  
  
6.  На вкладке **Свойства соединения** в списке **Соединение с базой данных** найдите на сервере базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и нажмите кнопку **Соединить**.  
  
7.  Чтобы открыть другое окно редактора запросов для того же соединения, на панели инструментов нажмите кнопку **Создать запрос**.  
  
8.  Чтобы сменить соединения, щелкните правой кнопкой мыши окно редактора запросов, наведите указатель на пункт **Соединение**и выберите команду **Изменить соединение**.  
  
9. В диалоговом окне **Подключение к SQL Server** выберите другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при его наличии, а затем нажмите кнопку **Соединить**.  
  
Эта новая возможность, предоставляемая редактором запросов, позволяет легко запускать один и тот же код на нескольких серверах. Это может быть полезно при обслуживании нескольких схожих серверов.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Добавление отступов](../../tools/sql-server-management-studio/lesson-2-2-adding-indentation.md)  
  
  
  
