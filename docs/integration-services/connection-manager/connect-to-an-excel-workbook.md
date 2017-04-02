---
title: "Подключение к книге Excel | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Excel [службы Integration Services]"
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Подключение к книге Excel
  Чтобы соединить пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с книгой Microsoft Office Excel, нужен диспетчер соединений Excel.  
  
 Создать такие диспетчеры соединений можно либо в области «Диспетчеры соединений» конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , либо с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Поставщики и драйверы для файлов Microsoft Excel и Access**  
  
 Если поставщики OLE DB и драйверы для файлов Microsoft Office еще не установлены, может потребоваться скачать их. Более поздние версии поставщика могут открывать файлы, созданные в более ранних версиях Excel.  
  
 Если на компьютере установлена 32-разрядная версия Office, необходимо установить драйверы для этой версии, а также убедиться, что вы запускаете мастер или создаваемый им пакет служб Integration Services в 32-разрядном режиме.  
  
|Версия Microsoft Office|Загрузить|  
|------------------------------|--------------|  
|2007 г.|[Системный драйвер Office 2007: компоненты подключения к данным](https://www.microsoft.com/en-us/download/details.aspx?id=23734)|  
|2010|[Среда выполнения Microsoft Access 2010](https://www.microsoft.com/en-us/download/details.aspx?id=10910)|  
|2013|[Среда выполнения Microsoft Access 2013](http://www.microsoft.com/en-us/download/details.aspx?id=39358)|  
  
### Создание диспетчера соединений Excel из области «Диспетчеры соединений»  
  
1.  Откройте пакет в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши в любом месте области **Диспетчеры соединений** и выберите **Создать соединение**.  
  
3.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **Excel**, а затем настройте диспетчер соединений.  
  
     Сведения о параметрах конфигурации для этого диспетчера соединений см. в разделе [Excel Connection Manager Editor](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
### Создание соединения Excel с помощью мастера импорта и экспорта SQL Server  
  
1.  Запустите 32-разрядную версию мастера экспорта и импорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  На странице **Выбор источника данных** выберите в поле **Источник данных**значение **Microsoft Excel**, а затем настройте соединение Excel.  
  
     Сведения о параметрах конфигурации для этого типа соединения см. в разделе [Excel Connection Manager Editor](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
## См. также  
 [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  