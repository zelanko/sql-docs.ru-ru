---
title: "Добавление пользовательского отчета в среду Management Studio | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-objects
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
caps.latest.revision: "6"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b682c71e77188ea46cea5f85590953c17d61bda
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="add-a-custom-report-to-management-studio"></a>Добавление пользовательского отчета в среду Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] В данном разделе описывается процесс создания простого отчета служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)], который сохраняется как файл в формате RDL, а затем добавляется в среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] в качестве пользовательского отчета. [!INCLUDE[ssRS](../../includes/ssrs_md.md)] могут создавать разнообразные сложные отчеты. Чтобы создать отчет по материалам этого раздела, на компьютере необходимо установить среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] . Для запуска пользовательского отчета с помощью среды [!INCLUDE[ssRS](../../includes/ssrs_md.md)] устанавливать на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] службы [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)]не обязательно.  
  
 
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a>Создание простого отчета, сохраняемого в файле в формате RDL  
  
1.  В меню **Пуск**наведите указатель на **Программы**, **Microsoft SQL Server**и щелкните **SQL Server Data Tools**.  
  
2.  В меню **Файл** укажите **Создать**, затем нажмите **Проект**.  
  
3.  В списке **Типы проектов** выберите значение **Проекты бизнес-аналитики**.  
  
4.  В списке **Шаблоны** щелкните **Мастер проекта сервера отчетов**.  
  
5.  В поле **Имя**введите **ConnectionsReport**и нажмите кнопку **ОК**.  
  
6.  На вводной странице **Мастер отчетов** нажмите кнопку **Далее**.  
  
7.  На странице **Выбор источника данных** введите в поле "Имя" имя для этого соединения с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)], а затем щелкните **Правка**.  
  
8.  В диалоговом окне **Свойства соединения** в поле **Имя сервера** введите имя экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
9. В поле **Выберите или введите имя базы данных** введите имя любой базы данных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], например [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject_md.md)], а затем нажмите кнопку **ОК**.  
  
10. На странице **Выбор источника данных** нажмите кнопку **Далее**.  
  
11. На странице **Создание запроса** в поле **Строка запроса** введите следующую инструкцию [!INCLUDE[tsql](../../includes/tsql_md.md)] , указывающую текущие соединения с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)], а затем нажмите кнопку **Далее**. В поле запроса мастера отчетов нельзя вводить параметры отчета. Более сложные отчеты необходимо создавать вручную.  
  
    **SELECT session_id, net_transport FROM sys.dm_exec_connections;**  
  
12. На странице **Выбор типа отчета** выберите параметр **Табличный**и нажмите кнопку **Готово**.  
  
13. На странице **Завершение работы мастера** в поле **Имя отчета** введите **ConnectionsReport**, затем нажмите кнопку **Готово** , чтобы создать и сохранить отчет.  
  
14. Закройте среду [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio_md.md)].  
  
15. Скопируйте файл **ConnectionsReport.rdl** в папку, созданную на сервере баз данных для пользовательских отчетов.  
  
### <a name="to-add-a-report-to-management-studio"></a>Добавление отчета в среду Management Studio  
  
-   В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)]щелкните узел в обозревателе объектов, укажите **Отчеты**и выберите **Пользовательские отчеты**. В диалоговом окне **Открытие файла** выберите папку пользовательских отчетов, укажите файл **ConnectionsReport.rdl** и нажмите кнопку **Открыть**.  
  
    При первом открытии пользовательского отчета из узла в обозревателе этот отчет добавляется к списку недавно использовавшихся **пользовательских отчетов** в контекстном меню этого узла. При первом открытии стандартного отчета он также отобразится в списке недавно использовавшихся **пользовательских отчетов**. Если удалить пользовательский отчет, при следующем выборе этого элемента появится запрос на удаление его из списка недавно использовавшихся отчетов.  
  
    1.  Чтобы изменить количество файлов, отображаемых в списке недавно использовавшихся, выберите в меню **Сервис** пункт **Параметры** , раскройте папку **Среда** и выберите **Общие**.  
  
    2.  Измените число в поле **Показать n файлов в списке недавно использованных**.  
  
## <a name="see-also"></a>См. также:  
[Пользовательские отчеты в среде Management Studio](../../ssms/object/custom-reports-in-management-studio.md)  
[Использование пользовательских отчетов совместно со свойствами узлов обозревателя объектов](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
[Отмена подавления предупреждений для пользовательских отчетов](../../ssms/object/unsuppress-run-custom-report-warnings.md)  
[службы SQL Server Reporting Services](http://msdn.microsoft.com/en-us/b8d18d3d-9db0-43e7-8286-7b46cc3a37ed)  
  
