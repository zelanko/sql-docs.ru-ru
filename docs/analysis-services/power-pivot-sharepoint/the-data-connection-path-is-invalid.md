---
title: "Недопустимый путь подключения к данным | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0f881435773a1a87969f1ad66c46cd9f55208071
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="the-data-connection-path-is-invalid"></a>Недопустимый путь подключения к данным
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Для книг Excel, содержащих [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] данных, службы Excel Services возвращает эту ошибку, если не удается подключиться к внедренным источникам данных.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Служба Excel Services настроена так, что разрешаются только соединения из файлов ODC, которые находятся в библиотеке доверенных подключений к данным.|  
|Текст сообщения|В книге путь подключения к данным указывает на файл, находящийся на локальном жестком диске, или является недопустимым URI. Следующие соединения не удалось обновить: данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] содержат подключения к внедренным данным. Для поддержки взаимодействия книги через срезы и фильтры в настройках службы Excel Services должен быть разрешен доступ к внешним данным с помощью данных внедренных соединений. Доступ к внешним данным требуется для получения данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , которые находятся на серверах [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  
  
## <a name="user-action"></a>Действие пользователя  
 Измените параметры конфигурации, разрешив соединения с внедренными источниками данных.  
  
1.  В разделе «Управление приложениями» центра администрирования выберите пункт **Управление приложениями служб**.  
  
2.  Щелкните **Приложение служб Excel**.  
  
3.  Щелкните **Надежные расположения файлов**.  
  
4.  Щелкните **http://** или расположение, которое требуется настроить.  
  
5.  На странице «Внешние данные» для параметра «Разрешить внешние данные» установите значение **Надежные библиотеки подключений к данным и внедренные**.  
  
6.  Нажмите кнопку **ОК**.  
  
 Или можно создать новое надежное местоположение для сайтов, содержащих книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , а затем изменить параметры конфигурации только для этого сайта. Дополнительные сведения см. в разделе [Создание надежного расположения для сайтов PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
