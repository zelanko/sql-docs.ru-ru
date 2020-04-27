---
title: Добавление, удаление или совместное использование диспетчера соединений в пакете | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], adding
- adding connection managers
ms.assetid: 6f2ba4ea-10be-4c40-9e80-7efcf6ee9655
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8b7d92800a2f5d55cf85ace3e7746d934b7474b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062010"
---
# <a name="add-delete-or-share-a-connection-manager-in-a-package"></a>Добавление, удаление или совместное использование диспетчера соединений в пакете
  Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержат множество диспетчеров соединений, предназначенных для соединения с различными источниками данных: реляционными базами данных, базами данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и файлами в форматах CSV и XML. Можно создать диспетчер соединений на уровне пакета или на уровне проекта. Диспетчер соединений, созданный на уровне проекта, доступен всем пакетам в проекте. Диспетчер соединений, созданный на уровне пакета, доступен только этому определенному пакету.  
  
 Диспетчеры соединений, созданные на уровне проекта, заменяют источники данных. Это делается для совместного использования соединений к источникам. Чтобы добавить диспетчер соединений на уровне проекта, проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] должен использовать модель развертывания проекта. Когда проект настроен для использования данной модели, в **обозревателе решений** появляется папка **Диспетчеры соединений**, а папка **Источники данных** удаляется из **обозревателя решений**.  
  
> [!NOTE]  
>  Если в пакете нужно использовать источники данных, проект необходимо преобразовать в модель развертывания пакета.  
>   
>  Дополнительные сведения об этих двух моделях см. в разделе [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md). Сведения о преобразовании проектов в модели развертывания проектов см. в разделе [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 Далее приведены процедуры, применяющиеся ко всем типам диспетчеров соединений, и описано выполнение следующих задач.  
  
-   [Добавление диспетчера соединений при создании пакета](#wizard)  
  
-   [Добавление диспетчера соединений в существующий пакет](#package)  
  
-   [Добавление диспетчера соединений на уровне проекта](#project)  
  
-   [Создание параметра для свойства диспетчера соединений](#parameter)  
  
-   [Удаление диспетчера соединений из пакета](#DeletePackageLevel)  
  
-   [Удаление общего диспетчера соединений (диспетчер соединений на уровне проекта)](#DeleteProjectLevel)  
  
##  <a name="to-add-a-connection-manager-when-creating-a-package"></a><a name="wizard"></a>Добавление диспетчера соединений при создании пакета  
  
-   Использование мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
     Помимо создания и настройки диспетчера соединений, этот мастер также поможет создать и настроить источники и назначения, используемые диспетчером соединений. Дополнительные сведения см. в разделе [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
##  <a name="to-add-a-connection-manager-to-an-existing-package"></a><a name="package"></a>Добавление диспетчера соединений в существующий пакет  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Чтобы сделать доступной область [!INCLUDE[ssIS](../includes/ssis-md.md)] Диспетчеры соединений **, выберите в конструкторе служб** вкладку **Поток управления** , **Поток данных** или **Обработчик события** .  
  
4.  Щелкните правой кнопкой мыши в любом месте области **Диспетчеры подключений** и выполните одной из следующих действий:  
  
    -   Щелкните тип диспетчера соединений для добавления его в пакет.  
  
         -или-  
  
    -   Если тип, который нужно добавить, не перечислен, щелкните **Создать соединение** , чтобы открыть окно **Добавление диспетчера соединений служб SSIS** , выберите тип диспетчера соединений и нажмите кнопку **ОК**.  
  
     Откроется пользовательское диалоговое окно для выбранного типа диспетчера соединений. Дополнительные сведения о типах диспетчеров соединений и доступных параметрах представлены в таблице ниже.  
  
    |Диспетчер соединений|Параметры|  
    |------------------------|-------------|  
    |[Диспетчер соединений ADO](connection-manager/ado-connection-manager.md)|[настройка диспетчера соединений OLE DB](configure-ole-db-connection-manager.md)|  
    |[Диспетчер соединений ADO.NET](connection-manager/ado-net-connection-manager.md)|[настройка диспетчера соединений ADO.NET](configure-ado-net-connection-manager.md)|  
    |[диспетчер соединений служб Analysis Services](connection-manager/analysis-services-connection-manager.md)|[Добавление диалогового окна  «Диспетчер соединений со службами Analysis Services" в справочник по пользовательскому интерфейсу](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер соединений с Excel](connection-manager/excel-connection-manager.md)|[редактор диспетчера соединений с Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[диспетчер соединения файлов](connection-manager/file-connection-manager.md)|[редактор диспетчера подключения файлов](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[диспетчер соединений с несколькими файлами](connection-manager/multiple-files-connection-manager.md)|[Добавление диспетчера соединения файлов диалогового окна пользовательского Интерфейса в справочник](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер соединений с неструктурированными файлами](connection-manager/flat-file-connection-manager.md)|[Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](general-page-of-integration-services-designers-options.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Столбцы")](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Дополнительно")](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Предварительный просмотр")](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[диспетчер соединения с несколькими неструктурированными файлами](connection-manager/multiple-flat-files-connection-manager.md)|[Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Общие")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Столбцы")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Дополнительно")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Предварительный просмотр")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[диспетчер FTP-соединений](connection-manager/ftp-connection-manager.md)|[редактор диспетчера FTP-сеансов](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[диспетчер HTTP-соединений](connection-manager/http-connection-manager.md)|[Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[диспетчер соединений MSMQ](connection-manager/msmq-connection-manager.md)|[редактор диспетчера MSMQ-сеансов](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[диспетчер соединений ODBC](connection-manager/odbc-connection-manager.md)|[Справочник по пользовательскому интерфейсу диспетчера соединений ODBC](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[диспетчер соединений OLE DB](connection-manager/ole-db-connection-manager.md)|[настройка диспетчера соединений OLE DB](configure-ole-db-connection-manager.md)|  
    |[SMO, диспетчер соединений](connection-manager/smo-connection-manager.md)|[редактор диспетчера соединений SMO](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[Диспетчер соединений SMTP](connection-manager/smtp-connection-manager.md)|[редактор диспетчера SMTP-сеансов](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[Диспетчер соединений SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)|[Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Диспетчер WMI-соединений](connection-manager/wmi-connection-manager.md)|[редактор диспетчера WMI-сеансов](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
     Область **Диспетчеры соединений** отображает добавленные диспетчеры соединений.  
  
5.  При необходимости можно щелкнуть правой кнопкой мыши диспетчер соединений, выбрать пункт **Переименовать**и изменить имя диспетчера соединений по умолчанию.  
  
6.  Чтобы сохранить обновленный пакет, щелкните **Сохранить выбранные элементы** в меню **Файл** .  
  
##  <a name="to-add-a-connection-manager-at-the-project-level"></a><a name="project"></a>Добавление диспетчера соединений на уровне проекта  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  В **Обозревателе решений**щелкните правой кнопкой мыши элемент **Диспетчеры соединений**и выберите команду **Новый диспетчер соединений**.  
  
3.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите тип диспетчера соединений и нажмите кнопку **Добавить**.  
  
     Откроется пользовательское диалоговое окно для выбранного типа диспетчера соединений. Дополнительные сведения о типах диспетчеров соединений и доступных параметрах представлены в таблице ниже.  
  
    |Диспетчер соединений|Параметры|  
    |------------------------|-------------|  
    |[Диспетчер соединений ADO](connection-manager/ado-connection-manager.md)|[настройка диспетчера соединений OLE DB](configure-ole-db-connection-manager.md)|  
    |[Диспетчер соединений ADO.NET](connection-manager/ado-net-connection-manager.md)|[настройка диспетчера соединений ADO.NET](configure-ado-net-connection-manager.md)|  
    |[диспетчер соединений служб Analysis Services](connection-manager/analysis-services-connection-manager.md)|[Добавление диалогового окна  «Диспетчер соединений со службами Analysis Services" в справочник по пользовательскому интерфейсу](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер соединений с Excel](connection-manager/excel-connection-manager.md)|[редактор диспетчера соединений с Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[диспетчер соединения файлов](connection-manager/file-connection-manager.md)|[редактор диспетчера подключения файлов](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[диспетчер соединений с несколькими файлами](connection-manager/multiple-files-connection-manager.md)|[Добавление диспетчера соединения файлов диалогового окна пользовательского Интерфейса в справочник](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер соединений с неструктурированными файлами](connection-manager/flat-file-connection-manager.md)|[Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](general-page-of-integration-services-designers-options.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Столбцы")](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Дополнительно")](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Предварительный просмотр")](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[диспетчер соединения с несколькими неструктурированными файлами](connection-manager/multiple-flat-files-connection-manager.md)|[Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Общие")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Столбцы")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Дополнительно")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Предварительный просмотр")](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[диспетчер FTP-соединений](connection-manager/ftp-connection-manager.md)|[редактор диспетчера FTP-сеансов](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[диспетчер HTTP-соединений](connection-manager/http-connection-manager.md)|[Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[диспетчер соединений MSMQ](connection-manager/msmq-connection-manager.md)|[редактор диспетчера MSMQ-сеансов](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[диспетчер соединений ODBC](connection-manager/odbc-connection-manager.md)|[Справочник по пользовательскому интерфейсу диспетчера соединений ODBC](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[диспетчер соединений OLE DB](connection-manager/ole-db-connection-manager.md)|[настройка диспетчера соединений OLE DB](configure-ole-db-connection-manager.md)|  
    |[SMO, диспетчер соединений](connection-manager/smo-connection-manager.md)|[редактор диспетчера соединений SMO](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[Диспетчер соединений SMTP](connection-manager/smtp-connection-manager.md)|[редактор диспетчера SMTP-сеансов](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[Диспетчер соединений SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)|[Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Диспетчер WMI-соединений](connection-manager/wmi-connection-manager.md)|[редактор диспетчера WMI-сеансов](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
     Добавленный диспетчер соединений появится в узле **Диспетчеры соединений** в **обозревателе решений**. Также он появится на вкладке **Диспетчеры соединений** в окне **Конструктор служб SSIS** для всех пакетов в проекте. Имя диспетчера соединений на этой вкладке будет иметь префикс **(проект)** для того, чтобы можно было отличить данный диспетчер соединений на уровне проекта от диспетчеров соединений на уровне пакета.  
  
4.  По желанию щелкните правой кнопкой мыши диспетчер соединений в окне **Обозреватель решений** в узле **Диспетчеры соединений** или на вкладке **Диспетчеры соединений** в окне **Конструктор служб SSIS** , нажмите кнопку **Переименовать**и измените имя диспетчера соединений, установленное по умолчанию.  
  
    > [!NOTE]  
    >  На вкладке **Диспетчеры соединений** окна **конструктора служб SSIS** невозможно перезаписать префикс **(проект)** из имени диспетчера соединений. Это сделано намеренно.  
  
##  <a name="to-create-a-parameter-for-a-connection-manager-property"></a><a name="parameter"></a>Создание параметра для свойства диспетчера соединений  
  
1.  В области **Диспетчеры соединений** щелкните правой кнопкой мыши диспетчер соединений, для которого необходимо создать параметр, и щелкните **Параметризировать**.  
  
2.  Настройка установок параметра в диалоговом окне **Параметризация** . Дополнительные сведения см. в разделе [Parameterize Dialog Box](../../2014/integration-services/parameterize-dialog-box.md).  
  
##  <a name="to-delete-a-connection-manager-from-a-package"></a><a name="DeletePackageLevel"></a>Удаление диспетчера соединений из пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Чтобы сделать доступной область [!INCLUDE[ssIS](../includes/ssis-md.md)] Диспетчеры соединений **, выберите в конструкторе служб** вкладку **Поток управления** , **Поток данных** или **Обработчик события** .  
  
4.  Щелкните правой кнопкой мыши диспетчер соединений, который необходимо удалить, и нажмите кнопку **Удалить**.  
  
     При удалении диспетчера соединений, связанного с элементом (например, с задачей «Выполнение SQL» или источником OLE DB), результат будет следующим.  
  
    -   На элементе пакета, использующем удаленный диспетчер соединений, отображается значок ошибки.  
  
    -   Пакет не проходит проверку.  
  
    -   Выполнение пакета невозможно.  
  
5.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
##  <a name="to-delete-a-shared-connection-manager-project-level-connection-manager"></a><a name="DeleteProjectLevel"></a>Удаление общего диспетчера соединений (диспетчер соединений на уровне проекта)  
  
1.  Для удаления диспетчера соединений на уровне проекта щелкните правой кнопкой мыши диспетчер соединений в узле **Диспетчеры соединений** в окне **Обозреватель решений** и нажмите кнопку **Удалить**. [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] отображает следующее предупреждающее сообщение:  
  
    > [!WARNING]  
    >  При удалении диспетчера соединений на уровне проекта, пакеты, использующие этот диспетчер соединений, могут не запуститься. Это действие нельзя отменить. Продолжить удаление диспетчера соединений?  
  
2.  Нажмите кнопку «ОК», чтобы удалить диспетчер соединений, или кнопку «Отмена», чтобы оставить диспетчер в проекте.  
  
    > [!NOTE]  
    >  Также можно удалить диспетчер соединений на уровне проекта на вкладке **Диспетчер соединений** в окне **Конструктор служб SSIS** , открытом для любого пакета в проекте. Удалить диспетчер можно, щелкнув правой кнопкой мыши диспетчер соединений на вкладке и выбрав **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Integration Services &#40;соединений&#41; SSIS](connection-manager/integration-services-ssis-connections.md)   
 [Задание свойств диспетчера соединений](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)  
  
  
