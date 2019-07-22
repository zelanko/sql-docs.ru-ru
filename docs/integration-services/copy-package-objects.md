---
title: Копирование объектов пакета | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d0d82dcc4e9caa3e61f5c8d33d034b9395e57fd6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057711"
---
# <a name="copy-package-objects"></a>Копирование объектов пакета

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  В этом разделе описано, как копировать элементы потока управления, потока данных и диспетчеров соединения внутри пакета или между пакетами.  
  
### <a name="to-copy-control-and-data-flow-items"></a>Копирование элементов управления и потока данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий нужные пакеты.  
  
2.  В обозревателе решений дважды щелкните пакеты, между которыми нужно выполнить копирование.  
  
3.  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] щелкните вкладку пакета, содержащего элементы для копирования, затем перейдите на вкладку **Поток управления**, **Поток данных**или **Обработчики событий** .  
  
4.  Выберите поток управления или элементы потока данных для копирования. Элементы можно выбирать по одному, нажав клавишу Shift и щелкая нужный элемент, либо выбрать группу элементов, перетаскивая указатель мыши через необходимые элементы.  
  
    > [!IMPORTANT]  
    >  Управление очередностью и пути, соединяющие элементы, при выборе двух соединяемых ими элементов автоматически не выбираются. Чтобы скопировать упорядоченный рабочий процесс (сегмент потока управления или потока данных), убедитесь, что были скопированы ограничение очередностью и пути.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Поток управления](../integration-services/control-flow/control-flow.md)   
 [Поток данных](../integration-services/data-flow/data-flow.md)   
 [Соединения в службах Integration Services (SSIS)](../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Копирование элементов проекта](https://msdn.microsoft.com/library/1606c54d-20f9-49f3-a4ef-caad83a772aa)  
  
  
