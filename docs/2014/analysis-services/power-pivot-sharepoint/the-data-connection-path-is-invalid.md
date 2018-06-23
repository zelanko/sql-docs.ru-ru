---
title: 'В книге путь подключения к данным указывает на файл, находящийся на локальном жестком диске, или является недопустимым URI. Следующие соединения не удалось обновить: данные PowerPivot | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5cb4c4794a59d203c119f09fba83fedeb7edb458
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101170"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>В книге путь подключения к данным указывает на файл, находящийся на локальном жестком диске, или является недопустимым URI. Следующие соединения не удалось обновить: Данные PowerPivot
  Служба Excel Services возвращает эту ошибку для книг Excel, содержащих данные PowerPivot, если она не может подключиться к внедренным источникам данных.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|PowerPivot для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Служба Excel Services настроена так, что разрешаются только соединения из файлов ODC, которые находятся в библиотеке доверенных подключений к данным.|  
|Текст сообщения|В книге путь подключения к данным указывает на файл, находящийся на локальном жестком диске, или является недопустимым URI. Следующие соединения не удалось обновить: Данные PowerPivot|  
  
## <a name="explanation"></a>Объяснение  
 Книги PowerPivot содержат подключения к внедренным данным. Для поддержки взаимодействия книги через срезы и фильтры в настройках службы Excel Services должен быть разрешен доступ к внешним данным с помощью данных внедренных соединений. Доступ к внешним данным требуется для получения данных PowerPivot, которые находятся на серверах PowerPivot в ферме.  
  
## <a name="user-action"></a>Действие пользователя  
 Измените параметры конфигурации, разрешив соединения с внедренными источниками данных.  
  
1.  В разделе «Управление приложениями» центра администрирования выберите пункт **Управление приложениями служб**.  
  
2.  Щелкните **Приложение служб Excel**.  
  
3.  Щелкните **Надежные расположения файлов**.  
  
4.  Щелкните **http://** или расположение, которое требуется настроить.  
  
5.  На странице «Внешние данные» для параметра «Разрешить внешние данные» установите значение **Надежные библиотеки подключений к данным и внедренные**.  
  
6.  Нажмите кнопку **ОК**.  
  
 Или можно создать новое надежное местоположение для сайтов, содержащих книги PowerPivot, а затем изменить параметры конфигурации только для этого сайта. Дополнительные сведения см. в разделе [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  