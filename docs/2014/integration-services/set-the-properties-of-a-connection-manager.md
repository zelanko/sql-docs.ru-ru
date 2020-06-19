---
title: Задание свойств диспетчера соединений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], modifying
- modifying connection managers
ms.assetid: 54793114-2198-4d80-8091-e241d5a5d13c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c8581771394ed40f740ea83407b9acd47c6f4ddd
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963244"
---
# <a name="set-the-properties-of-a-connection-manager"></a>Задание свойств диспетчера соединений
  Все диспетчеры соединений могут быть настроены в окне **Свойства** .  
  
 Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предлагают пользовательские диалоговые окна для изменения различных типов диспетчеров подключений в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Диалоговое окно имеет различные наборы настроек в зависимости от типа диспетчера соединений.  
  
### <a name="to-modify-a-connection-manager-using-the-properties-window"></a>Изменение диспетчера соединений в окне «Свойства»  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  В конструкторе служб SSIS перейдите на вкладку **Поток управления** , **Поток данных** или **Обработчик событий** , чтобы получить доступ к области **Диспетчеры соединений** .  
  
4.  Правой кнопкой мыши щелкните диспетчер подключений и выберите пункт **Свойства**.  
  
5.  В окне **Свойства** измените значения свойств. Окно **Свойства** предоставляет доступ к некоторым свойствам, которые не настраиваются через обычный редактор диспетчера соединений.  
  
6.  Нажмите кнопку **ОК**.  
  
7.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
### <a name="to-modify-a-connection-manager-using-a-connection-manager-dialog-box"></a>Изменение диспетчера соединений в диалоговом окне диспетчера соединений  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Чтобы сделать доступной область [!INCLUDE[ssIS](../includes/ssis-md.md)] Диспетчеры соединений **, выберите в конструкторе служб** вкладку **Поток управления** , **Поток данных** или **Обработчик события** .  
  
4.  В области **Диспетчеры соединений** дважды щелкните нужный диспетчер подключений для открытия диалогового окна **Диспетчер соединений** . Дополнительные сведения о конкретных типах диспетчеров соединений и настройках каждого из них см. в следующей таблице.  
  
    |Диспетчер соединений|Варианты|  
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
  
5.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;соединений&#41; SSIS](connection-manager/integration-services-ssis-connections.md)   
 [Добавление, удаление или совместное использование диспетчера соединений в пакете](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
  
