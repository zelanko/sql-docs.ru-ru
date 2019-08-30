---
title: Назначение "ADO.NET" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6126a352377e988c08a11211d12bb8bc77e93f7
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153972"
---
# <a name="ado-net-destination"></a>Назначение «ADO.NET»
  Назначение ADO NET загружает данные в различные базы данных, совместимые с [!INCLUDE[vstecado](../../includes/vstecado-md.md)], которые используют таблицу или представление базы данных. Можно загрузить эти данные в существующую таблицу или представление либо создать новую таблицу и загрузить в нее данные.  
  
 Вы можете использовать назначение "ADO.NET" для соединения с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Соединение с базой данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с помощью OLE DB не поддерживается. Дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)]см. в разделе [Общие рекомендации и ограничения (база данных SQL Azure)](https://go.microsoft.com/fwlink/?LinkId=248228).  
  
## <a name="troubleshooting-the-ado-net-destination"></a>Устранение неполадок, связанных с назначением «ADO.NET»  
 Вы можете протоколировать вызовы, сделанные назначением «ADO.NET» к внешним поставщикам данных. Эти функции ведения журналов можно использовать для устранения неполадок при сохранении данных во внешних источниках данных, выполняемых назначением ADO NET. Чтобы протоколировать вызовы, выполненные назначением ADO NET к внешнему поставщику данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuring-the-ado-net-destination"></a>Настройка назначения «ADO.NET»  
 Чтобы подключиться к источнику данных, назначение использует диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] . Диспетчером соединений указывается поставщик [!INCLUDE[vstecado](../../includes/vstecado-md.md)] для использования. Дополнительные сведения см. в разделе [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).  
  
 Назначение ADO NET содержит сопоставления между входными столбцами и столбцами в источнике данных назначения. Не обязательно сопоставлять входные столбцы всем целевым столбцам. Однако свойства некоторых целевых столбцов могут требовать сопоставления с входными столбцами. В противном случае могут происходить ошибки. Например, если целевой столбец не допускает значений NULL, ему должен быть сопоставлен входной столбец. Кроме того, типы данных сопоставленных столбцов должны быть совместимыми. Например, нельзя сопоставить входной столбец строкового типа с целевым столбцом числового типа данных, если поставщик [!INCLUDE[vstecado](../../includes/vstecado-md.md)] не поддерживает такое сопоставление.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает вставку текста в столбцы, для которых установлен тип данных image. Дополнительные сведения о типах значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql).  
  
> [!NOTE]  
>  Назначение ADO NET не поддерживает сопоставление входного столбца типа DT_DBTIME столбцу базы данных типа datetime. Дополнительные сведения о типах данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных служб Integration Services](integration-services-data-types.md).  
  
 Назначение «ADO.NET» имеет один обычный вход и один вывод ошибок на выходе.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор назначения ADO NET** , см. в одном из следующих разделов:  
  
-   [Редактор назначения ADO.NET (страница "Диспетчер соединений")](../ado-net-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения ADO.NET (страница "Сопоставления")](../ado-net-destination-editor-mappings-page.md)  
  
-   [Редактор назначения ADO.NET (страница "Вывод ошибок")](../ado-net-destination-editor-error-output-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Common Properties](../common-properties.md)  
  
-   [Пользовательские свойства ADO NET](ado-net-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
  
