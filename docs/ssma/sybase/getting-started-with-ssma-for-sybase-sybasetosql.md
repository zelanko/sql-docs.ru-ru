---
title: Начало работы с SSMA для SAP ASE (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: f07f230f52fee5707084c01060e92220b35cb75c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029124"
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>Начало работы с SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для SAP ASE позволяет быстро, преобразование схем баз данных SAP Adaptive Server Enterprise (ASE), чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure, отправьте полученный схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure и переноса данных из SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных Azure SQL.  
  
В этом разделе представлен процесс установки, а затем ознакомиться с пользовательским интерфейсом SSMA.  
  
## <a name="installing-and-licensing-ssma"></a>Установка и лицензирования SSMA  
Чтобы использовать SSMA, сначала необходимо установить SSMA клиентскую программу на компьютере с доступом к как исходного экземпляра служб SAP ASE, так и на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Использование миграции данных на сервере, необходимо установить пакет расширений и по крайней мере один из поставщиков SAP ASE (OLE DB или ADO.NET) на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти компоненты поддерживают перенос данных и эмуляции функций системы SAP ASE. Инструкции по установке см. в разделе [Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md).  
  
Для запуска SSMA, нажмите кнопку **запустить**, пункты **все программы**, пункты  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant для Sybase**, а затем выберите  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant для Sybase**. При первом запуске SSMA, появится диалоговое окно лицензирования. SSMA необходимо лицензировать с помощью идентификатора Windows Live ID, прежде чем можно будет использовать SSMA. Лицензирования инструкции входят в состав инструкции по установке в [Установка SSMA для Sybase клиента &#40;SybaseToSQL&#41; ](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) раздела.  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA для интерфейса пользователя SAP ASE  
После SSMA установлен и лицензирован, SSMA можно использовать для переноса баз данных SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Он позволяет ознакомиться с пользовательским интерфейсом SSMA, прежде чем начать. В примере ниже показан пользовательский интерфейс для SSMA, включая обучающие ресурсы для метаданных, метаданные, панелей инструментов, область вывода и область списка ошибок:  
  
![SSMA для SAP ASE пользовательский интерфейс](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA для SAP ASE пользовательского интерфейса")  
  
Чтобы начать миграцию, необходимо сначала создать новый проект. Затем вы подключитесь к SAP ASE. После успешного подключения иерархию баз данных SAP ASE будет отображаться в обозревателе метаданных Sybase. После этого можно объектов щелкните правой кнопкой мыши в обозревателе метаданных Sybase для выполнения задач, таких как создание отчетов, которые оценивают преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Вы также можете выполнить эти задачи с помощью панели инструментов и меню.  
  
Также необходимо подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. После успешного подключения иерархию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных Azure SQL будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure. После преобразования схем SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure, выберите преобразованный схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure и затем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
После загрузки схем, преобразованное в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure, можно вернуться в обозреватель метаданных Sybase и перенести данные из баз данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или баз данных Azure SQL.  
  
Дополнительные сведения об этих задачах и порядок их выполнения см. в разделе [миграция SAP ASE баз данных в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md).  
  
Ниже описаны возможности пользовательского интерфейса SSMA.  
  
### <a name="metadata-explorers"></a>Обучающие ресурсы для метаданных  
SSMA содержит два проводников метаданных для просмотра и выполнения действий в SAP ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или баз данных Azure SQL.  
  
#### <a name="sybase-metadata-explorer"></a>Обозреватель метаданных Sybase  
Обозреватель метаданных Sybase отображаются сведения о базах данных на экземпляре источника SAP ASE.  
  
С помощью обозревателя метаданных Sybase, можно выполнять следующие задачи:  
  
-   Обзор таблиц в каждой базе данных.  
  
-   Выберите объекты для преобразования, а затем преобразовать объекты для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure. Дополнительные сведения см. в разделе [преобразование объектов базы данных SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
-   Выберите объекты для переноса данных, а затем перенести данные из этих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Дополнительные сведения см. в разделе [переноса данных SAP ASE на SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server или обозреватель метаданных SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
Можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure, чтобы выбрать преобразованных объектов базы данных SAP ASE, а затем загрузить (синхронизации) этих объектов в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
Дополнительные сведения см. в разделе [загрузка преобразовать объекты базы данных в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозреватель метаданных находятся вкладки, которые описывают выбранного объекта. Например если выбрать таблицу в обозревателе метаданных Sybase, шесть вкладок: **Таблица**, **SQL**, **сопоставление типов**, **данных**, **свойства**, и **отчета**. **Отчетов** вкладка содержит сведения только в том случае, после создания отчета, содержащего выбранный объект. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure, отображается три вкладки: **Таблица**, **SQL**, и **данных**.  
  
Большинство параметров метаданных доступны только для чтения. Тем не менее можно изменить следующие метаданные:  
  
-   В обозревателе метаданных Sybase можно изменить процедуры и сопоставления типов. Внести эти изменения, перед началом преобразования схемы.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure, можно изменить [!INCLUDE[tsql](../../includes/tsql-md.md)] для хранимых процедур. Внести эти изменения, прежде чем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Изменения, внесенные в обозревателе метаданных, отражаются в метаданные проекта, не в исходной или целевой базы данных.  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA имеет две панели: панель инструментов проекта и инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панели инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, подключении к SAP ASE и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Эти кнопки команды похожи на **файл** меню.  
  
#### <a name="the-migration-toolbar"></a>На панели инструментов миграции  
Панель инструментов миграции содержит следующие команды:  
  
|Кнопка|Компонент|  
|----------|------------|  
|**Создание отчета**|Преобразует выбранные объекты SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, а затем создает отчет, показывающий, насколько успешно была преобразование.<br /><br />Эта команда доступна только в том случае, если выбраны объекты в обозревателе метаданных Sybase.|  
|**Преобразовать схему**|Преобразует выбранные объекты SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбраны объекты в обозревателе метаданных Sybase.|  
|**Перенос данных**|Перенос данных из базы данных SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Перед выполнением этой команды, необходимо преобразовать схемы SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure и затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбраны объекты в обозревателе метаданных Sybase.|  
|**Stop**|Останавливает текущий процесс, например преобразование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure.|  
  
### <a name="menus"></a>Меню  
SSMA содержит следующие меню:  
  
|Меню|Описание|  
|--------|---------------|  
|**Файл**|Содержит команды для работы с проектами, подключении к SAP ASE и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.|  
|**Изменить**|Содержит команды для поиска и работа с текстом на страницах сведения, такие как копирование [!INCLUDE[tsql](../../includes/tsql-md.md)] из области сведений SQL. Также содержит **управление закладками** параметр, где вы увидите список существующих закладок воспользуйтесь. Кнопки в правой части диалогового окна можно использовать для управления закладки.|  
|**Вид**|Содержит **обучающие ресурсы для синхронизации метаданных** команды. Это синхронизирует объекты между обозреватель метаданных Sybase и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure. Также содержит команды для отображения и скрытия **вывода** и **список ошибок** областей и параметр **макеты** для управления макетов.|  
|**Инструменты**|Команды для создания отчетов, экспорт данных и перенести объекты и данные. Также предоставляет доступ к **глобальные параметры** и **параметры проекта** диалоговым окнам.|  
|**Тест-инженер**|Содержит команды, чтобы создать тестовые случаи, просматривать результаты тестов и команды для управления резервными копиями базы данных.|  
|**Справка**|Предоставляет доступ к справке SSMA и **о** диалоговое окно.|  
  
### <a name="output-pane-and-error-list-pane"></a>Области вывода и список ошибок  
**Представление** меню доступны команды для переключения видимости области вывода и список ошибок:  
  
-   На панели вывода показывает сообщения о состоянии из SSMA во время преобразования объекта, объект синхронизации и переноса данных.  
  
-   На панели списка ошибок отображаются ошибки, предупреждения и информационные сообщения, в списке, можно сортировать.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных SAP ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Справочник по пользовательскому интерфейсу &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
