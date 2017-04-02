---
title: "Назначение &#171;ADO.NET&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.adonetdest.f1"
helpviewer_keywords: 
  - "назначения [службы Integration Services], ADO.NET"
  - "ADO.NET, назначение"
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Назначение &#171;ADO.NET&#187;
  Назначение ADO NET загружает данные в различные базы данных, совместимые с [!INCLUDE[vstecado](../../includes/vstecado-md.md)], которые используют таблицу или представление базы данных. Можно загрузить эти данные в существующую таблицу или представление либо создать новую таблицу и загрузить в нее данные.  
  
 Вы можете использовать назначение "ADO.NET" для соединения с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]. Соединение с базой данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с помощью OLE DB не поддерживается. Дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)] см. в разделе [Общие рекомендации и ограничения (база данных SQL Windows Azure)](http://go.microsoft.com/fwlink/?LinkId=248228).  
  
## Устранение неполадок, связанных с назначением «ADO.NET»  
 Вы можете протоколировать вызовы, сделанные назначением «ADO.NET» к внешним поставщикам данных. Эти функции ведения журналов можно использовать для устранения неполадок при сохранении данных во внешних источниках данных, выполняемых назначением ADO NET. Чтобы протоколировать вызовы, выполненные назначением ADO NET к внешнему поставщику данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## Настройка назначения «ADO.NET»  
 Чтобы подключиться к источнику данных, назначение использует диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] . Диспетчером соединений указывается поставщик [!INCLUDE[vstecado](../../includes/vstecado-md.md)] для использования. Дополнительные сведения см. в разделе [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
 Назначение ADO NET содержит сопоставления между входными столбцами и столбцами в источнике данных назначения. Не обязательно сопоставлять входные столбцы всем целевым столбцам. Однако свойства некоторых целевых столбцов могут требовать сопоставления с входными столбцами. В противном случае могут происходить ошибки. Например, если целевой столбец не допускает значений NULL, ему должен быть сопоставлен входной столбец. Кроме того, типы данных сопоставленных столбцов должны быть совместимыми. Например, нельзя сопоставить входной столбец строкового типа с целевым столбцом числового типа данных, если поставщик [!INCLUDE[vstecado](../../includes/vstecado-md.md)] не поддерживает такое сопоставление.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает вставку текста в столбцы, для которых установлен тип данных image. Дополнительные сведения о типах значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
>  Назначение ADO NET не поддерживает сопоставление входного столбца типа DT_DBTIME столбцу базы данных типа datetime. Дополнительные сведения о типах данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Назначение «ADO.NET» имеет один обычный вход и один вывод ошибок на выходе.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор назначения ADO NET** , см. в одном из следующих разделов:  
  
-   [Редактор назначения ADO.NET (страница "Диспетчер соединений")](../../integration-services/data-flow/ado-net-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения ADO.NET (страница "Сопоставления")](../../integration-services/data-flow/ado-net-destination-editor-mappings-page.md)  
  
-   [Редактор назначения ADO.NET (страница "Вывод ошибок")](../../integration-services/data-flow/ado-net-destination-editor-error-output-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../Topic/Common%20Properties.md)  
  
-   [Пользовательские свойства ADO NET](../../integration-services/data-flow/ado-net-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  