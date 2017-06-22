---
title: "Добавление новых элементов в проект | Документация Майкрософт"
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
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6740b2a6b1ba8842170e0d1f73aeb0b5f198caf2
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="add-new-items-to-a-project"></a>Добавление в проект новые элементы
Для расширения возможностей приложения в проект можно добавлять новые элементы. В качестве нового элемента может быть выбран запрос или соединение. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] имеет два типа проектов: проект скрипта [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и проект скрипта служб Analysis Services. Тип проекта определяет элементы, которые можно добавлять в проект. Например, запрос [!INCLUDE[tsql](../../includes/tsql_md.md)] (SQL-файл) можно добавить в проект скрипта [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , но нельзя добавить в проект скрипта служб Analysis Services.  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] не разрешает добавлять папки внутри проекта. Для организации работы следует создавать несколько проектов внутри решения.  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a>Добавление нового запроса в существующий проект  
  
1.  Выберите целевой проект в обозревателе решений.  
  
2.  В меню **Проект** выберите **Добавить новый элемент**.  
  
3.  Выберите категорию в левой панели диалогового окна **Добавление нового элемента** .  
  
4.  В правой панели выберите шаблон запроса, а затем нажмите кнопку **Добавить**. Новый запрос будет добавлен в папку **Запросы** проекта.  
  
5.  В диалоговом окне **Подключиться к ядру СУБД** задайте соединение для нового запроса, затем нажмите **Соединить**. Если нет необходимости связывать подключение с новым запросом, в диалоговом окне соединения можно нажать кнопку **Отмена** .  
  
6.  При необходимости переименуйте запрос в обозревателе решений.  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a>Добавление нового соединения в существующий проект  
  
1.  Выберите целевой проект в обозревателе решений.  
  
2.  В меню **Проект** выберите **Добавить новый элемент**.  
  
3.  В левой панели выберите пункт **Соединение** .  
  
4.  В правой панели выберите пункт **Новое соединение** , а затем нажмите кнопку **Добавить**.  
  
5.  В диалоговом окне **Подключиться к ядру СУБД** задайте соединение для нового запроса, затем нажмите **Соединить**. Новое соединение будет добавлено в папку **Соединение** проекта.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Связывание расширений файлов с редактором кода](http://msdn.microsoft.com/en-us/193630f4-93de-4950-8f36-68702531f925)  
[Добавление существующих элементов в проект](../../ssms/solution/add-existing-items-to-a-project.md)  
[Перемещение или удаление элемента или проекта](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  

