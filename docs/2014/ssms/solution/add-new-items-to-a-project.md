---
title: Добавление новых элементов в проект | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 37d752470586e0324f81a41ee1bb70483fee9fcc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149121"
---
# <a name="add-new-items-to-a-project"></a>Добавление в проект новые элементы
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
  
## <a name="see-also"></a>См. также  
 [Обозреватель решений](solution-explorer.md)   
 [Связывание расширения файла с редактором кода](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)   
 [Добавление существующих элементов в проект](add-existing-items-to-a-project.md)   
 [Перемещение или удаление элемента или проекта](remove-or-delete-an-item-or-project.md)  
  
  
