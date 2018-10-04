---
title: Essentials пакета служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 91aa24a11c7d4587500ab7154f582bb47b8f8c4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193244"
---
# <a name="ssis-package-essentials"></a>Основы работы с пакетами служб SSIS
  Пакет представляет собой объект, который реализует функциональность служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по извлечению, преобразованию и загрузке данных. Пакет создается с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Его можно также создать с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] либо мастера проекта соединений служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Дополнительные сведения [создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) в конструкторе служб SSIS и [мастер импорта проекта](../../2014/integration-services/import-project-wizard.md).  
  
 Основной пакет включает следующие элементы.  
  
 **Элементы потока управления**  
 Эти обязательные элементы выполняют различные функции, поддерживают структуру и управляют порядком выполнения элементов. Основными элементами потока управления являются задачи, контейнеры и управления очередностью. В пакете должен быть по крайней мере один элемент потока управления.  
  
 Дополнительные сведения см. в статье [Control Flow](control-flow/control-flow.md).  
  
 **Элементы потока данных**  
 Эти необязательные элементы извлекают, изменяют и загружают данные в источники данных. Основными элементами потока данных являются источники, преобразования и назначения. Присутствие каких-либо элементов потока данных в пакете необязательно.  
  
 Дополнительные сведения см. в статье [Data Flow](data-flow/data-flow.md).  
  
 Пример создания основного пакета см. в разделе [занятии 1: Создание проекта и основного пакета](lesson-1-create-a-project-and-basic-package-with-ssis.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)  
  
-   [Добавление задачи или контейнера в поток управления или удаление их из него](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Задание свойств задач или контейнеров](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [Добавление или удаление компонента в потоке данных](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a>См. также  
  
1.  Видеоматериал [Создание основного пакета (видеоматериал SQL Server)](http://go.microsoft.com/fwlink/?LinkId=131023)на сайте MSDN.Microsoft.com  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; пакетов](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Управление очередностью](control-flow/precedence-constraints.md)  
  
  
