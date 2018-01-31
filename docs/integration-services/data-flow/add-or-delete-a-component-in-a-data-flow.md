---
title: "Добавление или удаление компонента в потоке данных | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d2a061024c6921bdc2feccc9c6372104b4a4c70e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a>Добавление или удаление компонента в потоке данных
  Компонентами потока данных являются источники, назначения и преобразования потока данных. Чтобы добавлять компоненты к потоку данных, необходимо включить задачу потока данных в поток управления пакета.  
  
 Следующие процедуры описывают способы добавления или удаления компонента в потоке данных пакета.  
  
### <a name="to-add-a-component-to-a-data-flow"></a>Добавление компонента к потоку данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Откройте вкладку **Поток управления** , а затем дважды щелкните задачу потока данных, содержащую поток данных, к которому необходимо добавить компонент.  
  
4.  В инструментарии разверните **Источники потока данных**, **Преобразования потока данных**или **Назначения потока данных**и перетащите элемент потока данных в область конструктора на вкладке **Поток управления** .  
  
5.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
### <a name="to-delete-a-component-from-a-data-flow"></a>Удаление компонента из потока данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** и дважды щелкните задачу потока данных, содержащую поток данных, из которого необходимо удалить компонент.  
  
4.  Щелкните правой кнопкой мыши компонент потока данных и выберите пункт **Удалить**.  
  
5.  Подтвердите операцию удаления.  
  
6.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Соединение компонентов в потоке данных](../../integration-services/data-flow/connect-components-in-a-data-flow.md)   
 [Отладка потока данных](../../integration-services/troubleshooting/debugging-data-flow.md)   
 [Поток данных](../../integration-services/data-flow/data-flow.md)  
  
  
