---
title: Разработка подключенной базы данных | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.SQLSERVEROBJECTEXPLORER
ms.assetid: 21f7f959-7b8e-4335-8681-bebcd957692c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 70fc970a214c001e00703ddaa79438d59e31e487
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105769"
---
# <a name="connected-database-development"></a>Разработка подключенной базы данных
В этом разделе описаны функции проектирования и работы с запросами к подключенной базе данных, предоставляемые SQL Server Data Tools.  
  
Теперь с помощью обозревателя объектов SQL Server в среде Visual Studio разработчики могут создавать, изменять и просматривать как объекты баз данных SQL Server 2008 или Microsoft SQL Server 2012, которые физически расположены на предприятии, так и объекты баз данных за его пределами, на сервере SQL Azure. Разработчики могут легко клонировать существующую производственную базу данных с переходом на испытательный экземпляр, выполнять над ней дополнительную работу по разработке, а затем снова публиковать изменения в производственной базе данных.  
  
> [!NOTE]  
> Инструкции этого раздела содержат ряд задач, которые могут выполняться последовательно.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
|[Как подключаться к базе данных и просматривать существующие объекты](../ssdt/how-to-connect-to-a-database-and-browse-existing-objects.md)|Подключение к базе данных и просмотр ее сущностей.|  
|[Как создать объекты базы данных с помощью конструктора таблиц](../ssdt/how-to-create-database-objects-using-table-designer.md)|Использование нового конструктора таблиц для проектирования таблиц и управления связями между таблицами.|  
|[Как обновить подключенную базу данных с помощью Power Buffer](../ssdt/how-to-update-a-connected-database-with-power-buffer.md)|Обновление подключенной базы данных без написания скриптов с инструкциями ALTER.|  
|[Диалоговое окно "Фильтрация и сортировка"](../ssdt/filter-and-sort-dialog-box.md)|Указать, какие данные должны отображаться в представлении данных.|  
|[Как создать объекты базы данных с помощью запросов](../ssdt/how-to-create-new-database-objects-using-queries.md)|Использование редактора Transact\-SQL для изменения и выполнения скриптов Transact\-SQL.|  
|[Как изменить существующую таблицу с помощью запросов](../ssdt/how-to-edit-an-existing-table-using-queries.md)|Написание скриптов Transact\-SQL для изменения определения таблицы или заполнения таблицы данными.|  
|[Как просмотреть и изменить данные в таблице](../ssdt/how-to-view-and-edit-data-in-a-table.md)|Использование редактора данных для просмотра или ввода данных в таблицу.|  
|[Как удалить объекты и разрешить зависимости](../ssdt/how-to-delete-objects-and-resolve-dependencies.md)|Переименование или удаление сущностей базы данных и настройка SQL Server Data Tools на автоматическое разрешение зависимостей между объектами.|  
|[Как клонировать существующую базу данных](../ssdt/how-to-clone-an-existing-database.md)|Создание базы данных разработки из производственной базы данных.|  
|[Извлечение, публикация и регистрация DACPAC-файлов](../ssdt/extract-publish-and-register-dacpac-files.md)|Показывает, как извлечь и опубликовать DACPAC-файлы.|  
  
## <a name="related-sections"></a>См. также  
[Управление таблицами и связями, а также исправление ошибок](../ssdt/manage-tables-relationships-and-fix-errors.md)  
  
