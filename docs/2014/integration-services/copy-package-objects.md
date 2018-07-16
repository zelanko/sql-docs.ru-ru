---
title: Копирование объектов пакета | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4e9ba66baccbaa7278766c0464851cbc9224e6dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296964"
---
# <a name="copy-package-objects"></a>Копирование объектов пакета
  В этом разделе описано, как копировать элементы потока управления, потока данных и диспетчеров соединения внутри пакета или между пакетами.  
  
### <a name="to-copy-control-and-data-flow-items"></a>Копирование элементов управления и потока данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий нужные пакеты.  
  
2.  В обозревателе решений дважды щелкните пакеты, между которыми нужно выполнить копирование.  
  
3.  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] щелкните вкладку пакета, содержащего элементы для копирования, затем перейдите на вкладку **Поток управления**, **Поток данных**или **Обработчики событий** .  
  
4.  Выберите поток управления или элементы потока данных для копирования. Элементы можно выбирать по одному, нажав клавишу Shift и щелкая нужный элемент, либо выбрать группу элементов, перетаскивая указатель мыши через необходимые элементы.  
  
    > [!IMPORTANT]  
    >  Управление очередностью и пути, соединяющие элементы, при выборе двух соединяемых ими элементов автоматически не выбираются. Чтобы скопировать упорядоченный рабочий процесс — сегмент потока управления или потока данных, — убедитесь, что были скопированы ограничение очередностью и пути.  
  
5.  Щелкните правой кнопкой мыши выбранный элемент и выберите **Копировать**.  
  
6.  Для копирования элементов в другой пакет щелкните нужный пакет и перейдите на соответствующую вкладку.  
  
    > [!IMPORTANT]  
    >  Невозможно скопировать поток данных в пакет, пока в нем нет ни одной задачи потока данных.  
  
7.  Щелкните правой кнопкой мыши и выберите **Вставить**.  
  
### <a name="to-copy-connection-managers"></a>Копирование диспетчеров соединений  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий нужный пакет.  
  
2.  Дважды щелкните пакет в обозревателе решений.  
  
3.  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] перейдите на вкладку **Поток управления**, **Поток данных**или **Обработчик события** .  
  
4.  В поле **Диспетчеры соединений** щелкните правой кнопкой мыши диспетчер подключений и выберите **Копировать**. Одновременно можно скопировать только один диспетчер соединений.  
  
5.  Для копирования элементов в другой пакет щелкните пакет, в который нужно их скопировать, затем перейдите на вкладку **Поток управления**, **Поток данных**или **Обработчик события** .  
  
6.  Щелкните правой кнопкой мыши **Диспетчеры соединений** и выберите **Вставить**.  
  
## <a name="see-also"></a>См. также  
 [Поток управления](control-flow/control-flow.md)   
 [Поток данных](data-flow/data-flow.md)   
 [Соединения в службах Integration Services (SSIS)](connection-manager/integration-services-ssis-connections.md)   
 [Копирование элементов проекта](../../2014/integration-services/copy-project-items.md)  
  
  
