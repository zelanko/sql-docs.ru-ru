---
title: Добавление пользовательского отчета в среду Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a860db611154f9f7a130ee6be90dd43a96b50af5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62510424"
---
# <a name="add-a-custom-report-to-management-studio"></a>Добавление пользовательского отчета в среду Management Studio
  В данном разделе описывается процесс создания простого отчета служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который сохраняется как файл в формате RDL, а затем добавляется в среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в качестве пользовательского отчета. [!INCLUDE[ssRS](../../includes/ssrs.md)] могут создавать разнообразные сложные отчеты. Чтобы создать отчет по материалам этого раздела, на компьютере необходимо установить среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] . Для запуска пользовательского отчета с помощью среды [!INCLUDE[ssRS](../../includes/ssrs.md)] устанавливать на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]не обязательно.  
  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a>Создание простого отчета, сохраняемого в файле в формате RDL  
  
1.  В меню **Пуск**наведите указатель на **Программы**, **Microsoft SQL Server**и щелкните **SQL Server Data Tools**.  
  
2.  В меню **Файл** укажите **Создать**, затем нажмите **Проект**.  
  
3.  В списке **Типы проектов** выберите значение **Проекты бизнес-аналитики**.  
  
4.  В списке **Шаблоны** щелкните **Мастер проекта сервера отчетов**.  
  
5.  В поле **Имя**введите **ConnectionsReport**и нажмите кнопку **ОК**.  
  
6.  На вводной странице **Мастер отчетов** нажмите кнопку **Далее**.  
  
7.  На странице **Выбор источника данных** введите в поле "Имя" имя для этого соединения с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], а затем щелкните **Правка**.  
  
8.  В диалоговом окне **Свойства соединения** в поле **Имя сервера** введите имя экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
9. В поле **Выберите или введите имя базы данных** введите имя любой базы данных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], а затем нажмите кнопку **ОК**.  
  
10. На странице **Выбор источника данных** нажмите кнопку **Далее**.  
  
11. На странице **Создание запроса** в поле **Строка запроса** введите следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] , указывающую текущие соединения с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], а затем нажмите кнопку **Далее**. В поле запроса мастера отчетов нельзя вводить параметры отчета. Более сложные отчеты необходимо создавать вручную.  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. На странице **Выбор типа отчета** выберите параметр **Табличный**и нажмите кнопку **Готово**.  
  
13. На странице **Завершение работы мастера** в поле **Имя отчета** введите **ConnectionsReport**, затем нажмите кнопку **Готово** , чтобы создать и сохранить отчет.  
  
14. Закройте среду [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
15. Скопируйте файл **ConnectionsReport.rdl** в папку, созданную на сервере баз данных для пользовательских отчетов.  
  
### <a name="to-add-a-report-to-management-studio"></a>Добавление отчета в среду Management Studio  
  
-   В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]щелкните узел в обозревателе объектов, укажите **Отчеты**и выберите **Пользовательские отчеты**. В диалоговом окне **Открытие файла** выберите папку пользовательских отчетов, укажите файл **ConnectionsReport.rdl** и нажмите кнопку **Открыть**.  
  
     При первом открытии пользовательского отчета из узла в обозревателе этот отчет добавляется к списку недавно использовавшихся **пользовательских отчетов** в контекстном меню этого узла. При первом открытии стандартного отчета он также отобразится в списке недавно использовавшихся **пользовательских отчетов**. Если удалить пользовательский отчет, при следующем выборе этого элемента появится запрос на удаление его из списка недавно использовавшихся отчетов.  
  
    1.  Чтобы изменить количество файлов, отображаемых в списке недавно использовавшихся, выберите в меню **Сервис** пункт **Параметры** , раскройте папку **Среда** и выберите **Общие**.  
  
    2.  Измените число в поле **Показать n файлов в списке недавно использованных**.  
  
## <a name="see-also"></a>См. также  
 [Пользовательские отчеты в среде Management Studio](custom-reports-in-management-studio.md)   
 [Использование пользовательских отчетов совместно со свойствами узлов обозревателя объектов](use-custom-reports-with-object-explorer-node-properties.md)   
 [Отмена подавления предупреждений для пользовательских отчетов](unsuppress-run-custom-report-warnings.md)   
 [Службы Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
