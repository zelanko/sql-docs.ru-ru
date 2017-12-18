---
title: "Диспетчер подключений Excel | Документы Майкрософт"
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: "41"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5785a2753b61cde59a5ed157d697b05a93796fc7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="excel-connection-manager"></a>Диспетчер соединений с Excel
  Диспетчер соединений Excel делает доступным соединение пакета с существующим файлом рабочей книги [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Источник "Excel" и назначение "Excel", которые включены в службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , используют диспетчер подключений Excel.  
  
 Если происходит добавление диспетчера соединений Excel к пакету, служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который будет разрешен как соединение Excel во время выполнения, задает свойства диспетчера соединений и добавляет диспетчер соединений к коллекции **Connections** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **EXCEL**.  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Настройка диспетчера соединений Excel  
 Чтобы настроить диспетчер соединений Excel, выполните следующее:  
  
-   Укажите путь файла рабочей книги Excel.  
  
    > [!NOTE]  
    >  Подключить защищенный паролем файл Excel нельзя.  
  
-   Укажите версию приложения Excel, использовавшуюся при создании файла.  
  
-   Укажите, содержатся ли имена столбцов в первой строке данных выбранного рабочего листа или диапазона.  
  
 Если диспетчер соединений Excel используется источником Excel, имена столбцов содержатся с извлеченными данными. Если он используется назначением Excel, имена столбцов включены в записанные данные.  
  
 Дополнительные сведения о поведении источников и назначений Excel см. в статьях [Excel Source](../../integration-services/data-flow/excel-source.md) и [Excel Destination](../../integration-services/data-flow/excel-destination.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Редактор диспетчера соединений с Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
 Дополнительные сведения о переходе между файлами в группе файлов Excel см. в разделе [Просмотр файлов и таблиц Excel с помощью контейнера "Цикл по каждому элементу"](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
## <a name="excel-connection-manager-editor"></a>редактор диспетчера соединений с Excel
  Диалоговое окно **Редактор диспетчера соединений с Excel** используется для добавления подключения к существующему или новому файлу книги [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .  
  
 Дополнительные сведения о диспетчере соединений с Excel см. в разделе [Диспетчер соединений с Excel](../../integration-services/connection-manager/excel-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Путь к файлу Excel**  
 Введите путь и имя существующего или нового файла книги Excel с расширением XLS.  
  
> [!NOTE]  
>  Подключить защищенный паролем файл Excel нельзя.  
  
> [!WARNING]  
>  **Редактор назначения Excel** автоматически создаст файл Excel при выборе **подключения Excel** , указывающего на новый или несуществующий файл. Затем выберите **Создать** для **имени листа Excel**.  
  
 **Обзор**  
 Для перехода в папку, в которой существует файл Excel или в которой будет создан новый файл, используйте диалоговое окно **Открыть** .  
  
 **Версия Excel**  
 Позволяет указать версию Microsoft Excel, в которой был создан файл.  
  
 **Первая строка содержит имена столбцов**  
 Позволяет указать, содержит ли первая строка данных выбранного листа имена столбцов. По умолчанию значение этого параметра равно **True**.  
  
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Компоненты подключения для файлов Microsoft Excel и Access
  
Если компоненты подключения для файлов Microsoft Office еще не установлены, может потребоваться скачать их. Скачать последнюю версию компонентов подключения для файлов Excel и Access можно на следующей странице: [Распространяемый компонент ядра СУБД Microsoft Access 2016](https://www.microsoft.com/download/details.aspx?id=54920).
  
Последняя версия компонентов позволяет открывать файлы, созданные в более ранних версиях Excel.

Если на компьютере установлена 32-разрядная версия Office, нужно установить 32-разрядную версию компонентов, а также убедиться в том, что пакет запускается в 32-разрядном режиме.

Если у вас есть подписка на Office 365, нужно скачать распространяемый компонент ядра СУБД Access 2016, а не среду выполнения Microsoft Access 2016. При запуске установщика может появиться сообщение о том, что невозможно установить скачанные компоненты вместе с компонентами Office, полученными с помощью технологии "нажми и работай". Чтобы обойти это сообщение, запустите установку в тихом режиме. Для этого откройте окно командной строки и запустите скачанный EXE-файл с параметром `/quiet`. Например:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Просмотр файлов и таблиц Excel с помощью контейнера "Цикл по каждому элементу"](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  
