---
title: Essentials пакета служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8cba1fb860d884b568fe132fc2b38ff50fbd480d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66055418"
---
# <a name="ssis-package-essentials"></a>Основы работы с пакетами служб SSIS
  Пакет представляет собой объект, который реализует функциональность служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по извлечению, преобразованию и загрузке данных. Пакет создается с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Его можно также создать с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] либо мастера проекта соединений служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Дополнительные сведения [создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) в конструкторе служб SSIS и [мастер импорта проекта](../../2014/integration-services/import-project-wizard.md).  
  
 Основной пакет включает следующие элементы.  
  
 **Элементы потока управления**  
 Эти обязательные элементы выполняют различные функции, поддерживают структуру и управляют порядком выполнения элементов. Основными элементами потока управления являются задачи, контейнеры и управления очередностью. В пакете должен быть по крайней мере один элемент потока управления.  
  
 Дополнительные сведения см. в разделе [Поток управления](control-flow/control-flow.md).  
  
 **Элементы потока данных**  
 Эти необязательные элементы извлекают, изменяют и загружают данные в источники данных. Основными элементами потока данных являются источники, преобразования и назначения. Присутствие каких-либо элементов потока данных в пакете необязательно.  
  
 Дополнительные сведения см. в статье [Поток данных](data-flow/data-flow.md).  
  
 Пример создания основного пакета см. в разделе [занятии 1: Создание проекта и основного пакета](lesson-1-create-a-project-and-basic-package-with-ssis.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)  
  
-   [Добавление задачи или контейнера в поток управления или удаление их из него](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Задание свойств задач или контейнеров](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [Добавление или удаление компонента в потоке данных](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a>См. также  
  
1.  Видеоматериал [Создание основного пакета (видеоматериал SQL Server)](https://go.microsoft.com/fwlink/?LinkId=131023) на сайте MSDN.Microsoft.com  
  
## <a name="see-also"></a>См. также  
 [Пакеты служб Integration Services (SSIS)](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Управление очередностью](control-flow/precedence-constraints.md)  
  
  
