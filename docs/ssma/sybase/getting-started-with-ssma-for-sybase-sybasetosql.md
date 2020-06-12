---
title: Начало работы с SSMA для SAP ASE (SybaseToSQL) | Документация Майкрософт
description: Узнайте о Помощник по миграции SQL Server (SSMA) для процесса установки SAP ASE и ознакомьтесь с пользовательским интерфейсом SSMA.
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 57a7a4d3f8bee507c11700f383d5bb02adb4172c
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293942"
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>Начало работы с SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) для SAP ASE позволяет быстро преобразовывать адаптивные схемы базы данных SAP (ASE) или схемы базы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных SQL Azure, передавать полученные схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure и переносить данные из SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure.  
  
В этом разделе описывается процесс установки, а затем мы познакомимся с пользовательским интерфейсом SSMA.  
  
## <a name="installing-and-licensing-ssma"></a>Установка и лицензирование SSMA  
Чтобы использовать SSMA, необходимо сначала установить клиентскую программу SSMA на компьютере, который может получить доступ как к исходному экземпляру SAP ASE, так и к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Чтобы использовать перенос данных на стороне сервера, необходимо установить пакет расширений и хотя бы один из поставщиков SAP ASE (OLE DB или ADO.NET) на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эти компоненты поддерживают перенос данных и эмуляцию системных функций SAP ASE. Инструкции по установке см. в разделе [Installing SSMA for SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md).  
  
Чтобы запустить SSMA, нажмите кнопку **Пуск**, укажите пункт **все программы**, выберите ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Помощник по миграции для Sybase**, а затем выберите ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Помощник по миграции для Sybase**. При первом запуске SSMA появляется диалоговое окно лицензирования. Для использования SSMA необходимо лицензировать SSMA с помощью идентификатора Windows Live ID. Инструкции по лицензированию включены в инструкции по установке, описанные в разделе [Installing SSMA for Sybase Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) .  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA для пользовательского интерфейса SAP ASE  
После установки и лицензирования SSMA можно использовать SSMA для переноса баз данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. Перед началом работы он поможет ознакомиться с пользовательским интерфейсом SSMA. На следующей схеме показан пользовательский интерфейс для SSMA, включая обозреватель метаданных, метаданные, панели инструментов, панель вывода и панель списка ошибок.  
  
![SSMA для пользовательского интерфейса SAP ASE](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA для пользовательского интерфейса SAP ASE")  
  
Чтобы начать миграцию, необходимо сначала создать новый проект. Затем вы подключаетесь к SAP ASE. После успешного подключения в обозревателе метаданных Sybase появится иерархия баз данных SAP ASE. Затем можно щелкнуть правой кнопкой мыши объекты в обозревателе метаданных Sybase, чтобы выполнять такие задачи, как создание отчетов, оценивающих преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure. Эти задачи также можно выполнить с помощью панелей инструментов и меню.  
  
Также необходимо подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. После успешного подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных появится иерархия или базы данных SQL Azure. После преобразования схем SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure выберите эти преобразованные схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных, а затем загрузите схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или.  
  
После загрузки преобразованных схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или их можно вернуться в обозреватель метаданных Sybase и перенести данные из баз данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
Дополнительные сведения об этих задачах и способах их выполнения см. [в статье миграция баз данных SAP ASE в SQL Server — база данных SQL Azure &#40;&#41;SybaseToSQL ](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md).  
  
В следующих разделах описываются функции пользовательского интерфейса SSMA.  
  
### <a name="metadata-explorers"></a>Обозреватель метаданных  
SSMA содержит два обозревателя метаданных для просмотра и выполнения действий в базах данных SAP ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure.  
  
#### <a name="sybase-metadata-explorer"></a>Обозреватель метаданных Sybase  
В обозревателе метаданных Sybase отображаются сведения о базах данных в исходном экземпляре SAP ASE.  
  
С помощью обозревателя метаданных Sybase можно выполнять следующие задачи:  
  
-   Просмотрите таблицы в каждой базе данных.  
  
-   Выберите объекты для преобразования, а затем преобразуйте объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис базы данных SQL Azure или. Дополнительные сведения см. в разделе [Преобразование объектов базы данных SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
-   Выберите объекты для переноса данных, а затем перенесите данные из этих объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. Дополнительные сведения см. [в статье Миграция данных SAP ASE в SQL Server — база данных SQL Azure &#40;&#41;SybaseToSQL ](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server или SQL Azure обозреватель метаданных  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или SQL Azure обозреватель метаданных отображает сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
Можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозреватель метаданных, чтобы выбрать преобразованные объекты базы данных SAP ASE, а затем загрузить (синхронизировать) эти объекты в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure.  
  
Дополнительные сведения см. [в разделе Загрузка преобразованных объектов базы данных в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозревателя метаданных находятся вкладки, описывающие выбранный объект. Например, если выбрать таблицу в обозревателе метаданных Sybase, отобразятся шесть вкладок: **Таблица**, **SQL**, **Сопоставление типов**, **данные**, **Свойства**и **отчет**. Вкладка **отчет** содержит сведения только после создания отчета, содержащего выбранный объект. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных, отобразятся три вкладки: **Таблица**, **SQL**и **данные**.  
  
Большинство параметров метаданных доступны только для чтения. Однако можно изменить следующие метаданные:  
  
-   В обозревателе метаданных Sybase можно изменять процедуры и сопоставления типов. Внесите эти изменения перед преобразованием схем.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных можно изменить [!INCLUDE[tsql](../../includes/tsql-md.md)] для хранимых процедур. Внесите эти изменения перед загрузкой схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Изменения, внесенные в обозревателе метаданных, отражаются в метаданных проекта, а не в исходных или целевых базах данных.  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA содержит две панели инструментов: панель инструментов проекта и панель инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панель инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, подключения к SAP ASE, а также подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных SQL Azure или к ней. Эти кнопки похожи на команды в меню **файл** .  
  
#### <a name="the-migration-toolbar"></a>Панель инструментов миграции  
Панель инструментов миграции содержит следующие команды:  
  
|Кнопка|Компонент|  
|----------|------------|  
|**Создавать отчет**|Преобразует выбранные объекты SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, а затем создает отчет, показывающий, как было выполнено преобразование.<br /><br />Эта команда доступна, только если в обозревателе метаданных Sybase выбраны объекты.|  
|**Преобразовать схему**|Преобразует выбранные объекты SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты базы данных SQL Azure или.<br /><br />Эта команда доступна, только если в обозревателе метаданных Sybase выбраны объекты.|  
|**Перенос данных**|Переносит данные из базы данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. Перед выполнением этой команды необходимо преобразовать схемы SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы базы данных SQL Azure или в нее, а затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure.<br /><br />Эта команда доступна, только если в обозревателе метаданных Sybase выбраны объекты.|  
|**Остановить**|Останавливает текущий процесс, например преобразование объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure.|  
  
### <a name="menus"></a>Меню  
SSMA содержит следующие меню:  
  
|Меню|Описание|  
|--------|---------------|  
|**Файл**|Содержит команды для работы с проектами, подключения к SAP ASE, а также подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных SQL Azure или к ней.|  
|**Edit** (Изменение)|Содержит команды для поиска и работы с текстом на страницах со сведениями, например для копирования [!INCLUDE[tsql](../../includes/tsql-md.md)] из области сведений о SQL. Также содержит параметр **Управление закладками** , в котором можно просмотреть список существующих закладок. Для управления закладками можно использовать кнопки в правой части диалогового окна.|  
|**Вид**|Содержит команду **Синхронизация обозревателей метаданных** . Это синхронизирует объекты между обозревателем метаданных Sybase и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателем метаданных. Также содержит команды для отображения и скрытия **выходных** и **Список ошибок** панелей и **макетов** параметров для управления макетами.|  
|**Инструменты**|Содержит команды для создания отчетов, экспорта данных и переноса объектов и данных. Также предоставляет доступ к диалоговым окнам **глобальные параметры** и **Параметры проекта** .|  
|**Тест-инженер**|Содержит команды для создания тестовых случаев, просмотра результатов тестов и команд для управления резервным копированием базы данных.|  
|**Справка**|Предоставляет доступ к справке SSMA и диалоговому окну " **о программе** ".|  
  
### <a name="output-pane-and-error-list-pane"></a>Область вывода и область Список ошибок  
Меню **вид** содержит команды для переключения видимости области вывода и список ошибок панели.  
  
-   В области вывода отображаются сообщения о состоянии от SSMA во время преобразования объектов, синхронизации объектов и переноса данных.  
  
-   В области Список ошибок отображаются сообщения об ошибках, предупреждениях и информационном списке, которые можно сортировать.  
  
## <a name="see-also"></a>Дополнительно  
[Миграция баз данных SAP ASE в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Справочник по пользовательскому интерфейсу &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
