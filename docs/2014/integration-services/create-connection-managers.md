---
title: Создание диспетчеров соединений | Документы Microsoft
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.connectionmanager.f1
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- packages [Integration Services], connections
- connection managers [Integration Services], creating
- SQL Server Integration Services packages, connections
ms.assetid: 6ca317b8-0061-4d9d-b830-ee8c21268345
caps.latest.revision: 54
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2ae1ccaa1e38d280c3d46fb4504f99df92254a9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095961"
---
# <a name="create-connection-managers"></a>Создание диспетчеров соединений
  Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] включают набор диспетчеров соединений для соответствия нуждам задач, подключающихся к разным серверам и источникам данных. Диспетчеры соединений используются компонентами потока данных, которые извлекают и загружают данные в разные типы хранилищ данных, и поставщиками журналов, которые записывают журналы на сервер, в таблицу [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в файл. Например, пакет с задачей «Отправка почты» использует тип диспетчера соединений SMTP, чтобы подключиться к SMTP-серверу. Пакет с заданием «Выполнение SQL» может использовать диспетчер соединений OLE DB, чтобы подключиться к базе данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](connection-manager/integration-services-ssis-connections.md).  
  
 Для автоматического создания и настройки диспетчеров подключений при создании пакета можно использовать мастер импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Он также поможет вам создать и настроить источники и назначения для диспетчеров подключений. Дополнительные сведения см. в статье [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
 Вручную создать новый диспетчер соединений и добавить его в существующий пакет можно в области **Диспетчеры соединений** на вкладках **Поток управления**, **Поток данных**и **Обработчики события** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] . В области **Диспетчер соединений** следует выбрать тип создаваемого диспетчера соединений и установить свойства этого диспетчера с помощью диалогового окна, доступного в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] . Дополнительные сведения см. в подразделе «Использование области "Диспетчеры соединений"» далее в этом разделе.  
  
 После того как диспетчер соединений добавлен к пакету, его можно использовать в задачах, контейнерах «цикл по каждому элементу», источниках, преобразованиях и целевых объектах. Дополнительные сведения см. в разделах [Задачи служб Integration Services](control-flow/integration-services-tasks.md), [Контейнер "цикл по каждому элементу"](control-flow/foreach-loop-container.md) и [Поток данных](data-flow/data-flow.md).  
  
## <a name="using-the-connection-managers-area"></a>Использование области «Диспетчеры соединений»  
 Диспетчеры соединений можно создавать на вкладках **Поток управления**, **Поток данных**или **Обработчики событий** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 Следующая диаграмма показывает область **Диспетчеры соединений** на вкладке **Поток управления** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 ![Снимок экрана: конструктор потока управления с пакетом](media/samplecontrolflow.gif "Снимок экрана: конструктор потока управления с пакетом")  
  
#### <a name="to-add-configure-or-delete-a-connection-manager-in-ssis-designer"></a>Добавление, изменение и удаление диспетчера соединений в конструкторе служб SSIS  
  
-   [Добавление, удаление или совместное использование диспетчера соединений в пакете](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
-   [Задание свойств диспетчера подключений](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)  
  
## <a name="32-bit-and-64-bit-providers-for-connection-managers"></a>32-разрядная и 64-разрядная версии поставщиков для диспетчеров соединений  
 Для многих поставщиков, используемых диспетчерами соединений, доступны 32-разрядная и 64-разрядная версии. Среда разработки служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — это 32-разрядная среда, поэтому в ней содержатся только 32-разрядные поставщики. Поэтому необходимо настроить диспетчер соединений для использования специального 64-разрядного поставщика, если 32-разрядная версия того же поставщика уже установлена.  
  
 Во время выполнения используется подходящая версия поставщика, даже если во время разработки указана 32-разрядная версия. 64-разрядная версия поставщика может быть запущена, даже если пакет запущен в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 У обеих версий поставщика один идентификатор. Чтобы предписать использование средой выполнения служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] доступной 64-разрядной версии поставщика, установите свойство Run64BitRuntime проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Если имеет значение свойства Run64BitRuntime `true`, среда выполнения находит и использует 64-разрядный поставщик; Если Run64BitRuntime `false`, среда выполнения находит и использует 32-разрядный поставщик. Дополнительные сведения о свойствах, которые можно настраивать в проектах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], см. в разделе [Службы Integration Services (SSIS) и среды Studio](integration-services-ssis-development-and-management-tools.md).  
  
## <a name="see-also"></a>См. также  
 [Поток управления](control-flow/control-flow.md)   
 [Поток данных](data-flow/data-flow.md)   
 [Службы Integration Services &#40;SSIS&#41; обработчики событий](integration-services-ssis-event-handlers.md)  
  
  