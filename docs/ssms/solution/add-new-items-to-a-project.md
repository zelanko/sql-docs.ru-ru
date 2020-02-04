---
title: Добавление в проект новые элементы
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 759d05b5817d88d170972267224f77a8e52e2d45
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251992"
---
# <a name="add-new-items-to-a-project"></a>Добавление в проект новые элементы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Для расширения возможностей приложения в проект можно добавлять новые элементы. В качестве нового элемента может быть выбран запрос или соединение. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] имеет два типа проектов: проект скрипта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и проект скрипта служб Analysis Services. Тип проекта определяет элементы, которые можно добавлять в проект. Например, запрос [!INCLUDE[tsql](../../includes/tsql-md.md)] (SQL-файл) можно добавить в проект скрипта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но нельзя добавить в проект скрипта служб Analysis Services.  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не разрешает добавлять папки внутри проекта. Для организации работы следует создавать несколько проектов внутри решения.  
  
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
[Связывание расширений файлов с редактором кода](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
[Добавление существующих элементов в проект](../../ssms/solution/add-existing-items-to-a-project.md)  
[Перемещение или удаление элемента или проекта](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
