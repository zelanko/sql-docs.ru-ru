---
title: Задание свойств диспетчера соединений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], modifying
- modifying connection managers
ms.assetid: 54793114-2198-4d80-8091-e241d5a5d13c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0148cca6701db9f28ed6dd7abccb1a1f00269510
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111864"
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
  
    |Диспетчер соединений|Параметры|  
    |------------------------|-------------|  
    |[Диспетчер подключений объектов данных ActiveX](connection-manager/ado-connection-manager.md)|[Настройка диспетчера подключений OLE DB](configure-ole-db-connection-manager.md)|  
    |[Диспетчер подключений ADO.NET](connection-manager/ado-net-connection-manager.md)|[Настройка диспетчера подключений ADO.NET](configure-ado-net-connection-manager.md)|  
    |[Диспетчер подключений служб Analysis Services](connection-manager/analysis-services-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений служб Analysis Services"](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений Excel](connection-manager/excel-connection-manager.md)|[Редактор диспетчера подключений Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Диспетчер подключений файлов](connection-manager/file-connection-manager.md)|[Редактор диспетчера подключений файлов](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Диспетчер подключений нескольких файлов](connection-manager/multiple-files-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений файлов"](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений неструктурированных файлов](connection-manager/flat-file-connection-manager.md)|[Редактор диспетчера подключений к неструктурированным файлам (страница "Общие")](general-page-of-integration-services-designers-options.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Столбцы")](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Дополнительно")](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Предварительный просмотр")](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Диспетчер подключений нескольких неструктурированных файлов](connection-manager/multiple-flat-files-connection-manager.md)|[Редактор диспетчера соединений с несколькими неструктурированными файлами &#40;страница "Общие"&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера соединений с несколькими неструктурированными файлами &#40;страница "столбцы"&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера соединений с несколькими неструктурированными файлами &#40;страница "Дополнительно"&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера соединений с несколькими неструктурированными файлами &#40;Предварительный просмотр страницы&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Диспетчер FTP-подключений](connection-manager/ftp-connection-manager.md)|[Редактор диспетчера FTP-подключений](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[Диспетчер HTTP-подключений](connection-manager/http-connection-manager.md)|[Редактор диспетчера HTTP-соединений &#40;страница сервера&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [Редактор диспетчера HTTP-соединений &#40;страницы прокси-сервера&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[Диспетчер подключений MSMQ](connection-manager/msmq-connection-manager.md)|[Редактор диспетчера подключений MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[Диспетчер подключений ODBC](connection-manager/odbc-connection-manager.md)|[Справочник по пользовательскому интерфейсу диспетчера подключений ODBC](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[Диспетчер подключений OLE DB](connection-manager/ole-db-connection-manager.md)|[Настройка диспетчера подключений OLE DB](configure-ole-db-connection-manager.md)|  
    |[Диспетчер подключений управляющих объектов SQL Server](connection-manager/smo-connection-manager.md)|[Редактор диспетчера подключений SMO](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[Диспетчер SMTP-подключений](connection-manager/smtp-connection-manager.md)|[Редактор диспетчера SMTP-подключений](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[Диспетчер подключений SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md)|[SQL Server Compact редактор диспетчера соединений Edition &#40;страница "подключения"&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [SQL Server Compact редактор диспетчера соединений Edition &#40;странице "все"&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Диспетчер WMI-подключений](connection-manager/wmi-connection-manager.md)|[Редактор диспетчера WMI-подключений](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
5.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Соединения в службах Integration Services (SSIS)](connection-manager/integration-services-ssis-connections.md)   
 [Добавление, удаление или совместное использование диспетчера соединений в пакете](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
  
