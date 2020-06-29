---
title: Основные сведения о пакете служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c4e3f6637c4e9fd65b0218b8489372355b3608f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421052"
---
# <a name="ssis-package-essentials"></a>Основы работы с пакетами служб SSIS
  Пакет представляет собой объект, который реализует функциональность служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по извлечению, преобразованию и загрузке данных. Пакет создается с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Его можно также создать с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] либо мастера проекта соединений служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Для получения дополнительных сведений [Создайте пакеты в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) в КОНСТРУКТОРЕ служб SSIS и [мастере импорта проектов](../../2014/integration-services/import-project-wizard.md).  
  
 Основной пакет включает следующие элементы.  
  
 **Элементы потока управления**  
 Эти обязательные элементы выполняют различные функции, поддерживают структуру и управляют порядком выполнения элементов. Основными элементами потока управления являются задачи, контейнеры и управления очередностью. В пакете должен быть по крайней мере один элемент потока управления.  
  
 Дополнительные сведения см. в разделе [Поток управления](control-flow/control-flow.md).  
  
 **Элементы потока данных**  
 Эти необязательные элементы извлекают, изменяют и загружают данные в источники данных. Основными элементами потока данных являются источники, преобразования и назначения. Присутствие каких-либо элементов потока данных в пакете необязательно.  
  
 Дополнительные сведения см. в статье [Поток данных](data-flow/data-flow.md).  
  
 Пример создания базового пакета см. [в разделе занятие 1. Создание проекта и основного пакета](lesson-1-create-a-project-and-basic-package-with-ssis.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)  
  
-   [Добавление задачи или контейнера в поток управления или удалить их из него](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Задание свойств задач или контейнеров](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [Добавление или удаление компонента в потоке данных](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a>См. также  
  
1.  Видеоматериал [Создание основного пакета (видеоматериал SQL Server)](https://go.microsoft.com/fwlink/?LinkId=131023)на сайте MSDN.Microsoft.com  
  
## <a name="see-also"></a>См. также  
 [Integration Services &#40;пакетов&#41; SSIS](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Управление очередностью](control-flow/precedence-constraints.md)  
  
  
